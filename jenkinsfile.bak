pipeline{
    agent any
    stages{
        stage('code checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/sumitkumarsingh7899896655/devops-automation.git']])
            }
        }
        stage('Docker Build and push') {
      steps {
        script {
              docker.withRegistry( 'https://registry.hub.docker.com', 'dockerhub' ) {
              def customImage = docker.build("sumitkumarsingh7899896655/jenkinsproject")
              customImage.push()
          }
      }
    }
}
        stage('Docker Scan') {
      steps {
        script {
              docker scan 
          }
      }
    }
    }
}