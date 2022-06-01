// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                // echo "HelloWorld"
//                bat 'javac HelloWorld.java'
//                 bat 'java -version'
//             }
//         }
//         stage('Run') {
//             steps {
//                 //echo "HelloWorld"
//                 bat 'java HelloWorld'
//             }
//         }
//     }
// }
pipeline {
environment {
registry = "anjalideshpande/Demo"
registryCredential = 'anjalideshpande'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/AnjaliDeshpande1/gitjenkinsintegration.git'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
stage('Cleaning up') {
steps{
sh "docker rmi $registry:$BUILD_NUMBER"
}
}
}
}
