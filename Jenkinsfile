// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 sh 'javac HelloWorld.java'
//             }
//         }
//         stage('Run') {
//             steps {
//                 sh 'java HelloWorld'
//             }
//         }
//     }
// }


pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}
