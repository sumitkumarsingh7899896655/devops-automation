pipeline{
    agent any
    stages{
        stage('code checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/gangarampadolkar93/jenkins_image.git']])
            }
        }
        stage('Docker Build and push') {
      steps {
        script {
              docker.withRegistry( 'https://registry.hub.docker.com', 'dockerhub' ) {
              def customImage = docker.build("gangarampadolkar/jenkins_image")
              customImage.push()
          }
      }
    }
}
    }
}