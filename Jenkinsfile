// pipeline {
//     agent any

//     tools {
//         maven 'Maven3'
//     }

//     stages {

//         stage('Checkout Code') {
//             steps {
//                 git 'https://github.com/Vardhangollapalli87/calculator-app.git'
//             }
//         }

//         stage('Build & Test') {
//             steps {
//                 bat 'mvn clean test'
//             }
//         }

//         stage('Package') {
//             steps {
//                 bat 'mvn package'
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Build succeeded!'
//             archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
//         }
//         failure {
//             echo 'Build failed!'
//         }
//     }
// }


pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Vardhangollapalli87/calculator-app.git'
            }
        }

        stage('Build & Test') {
            steps {
                bat 'mvn clean test'
            }
        }

        stage('Package JAR') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Install to Local Repo') {
            steps {
                bat 'mvn install'
            }
        }
    }

    post {
        success {
            echo 'Library JAR packaged and installed successfully'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo 'Build failed'
        }
    }
}
