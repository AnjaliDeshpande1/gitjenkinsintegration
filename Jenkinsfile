pipeline {
  environment {
  registry = "anjalideshpande/demo"
  registryCredential = '57d4e0bf-5590-4ff0-bebb-0f7e10acd3c8'
  dockerImage = ''
}
agent any
  
stages {
        stage('Build image') 
        {
          steps{
            script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
         }
         stage('Deploy the image') 
         {
            steps{
              script {
                  docker.withRegistry( '', registryCredential ) 
                      {
                        dockerImage.push()
                      }
                  }
                }
          }
          stage('Cleaning up') {
              steps{
                  bat "docker rmi $registry:$BUILD_NUMBER"
              }
          }
  }
}
