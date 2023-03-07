pipeline{
    agent any
    tools {
        maven 'MAVEN'
    }
	environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
    stages {
        stage('Build Maven') {
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sumitkumarsingh7899896655/devops-automation.git']])

                bat "mvn -Dmaven.test.failure.ignore=true clean package"
                
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                  bat 'docker build -t sumitkumarsingh7899896655/devops-automation .'
                }
            }
        }
    stage('Login to Docker ') {
      steps {
        bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
		bat 'echo Successfully logged in Docker'
      }
    }
    stage('Push to Docker hub') {
      steps {
        bat 'docker push sumitkumarsingh7899896655/jenkinsproject'
      }
    }
	}
}
