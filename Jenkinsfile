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


// pipeline {
//     agent any

//     stages {

//         stage('Checkout Code') {
//             steps {
//                 git branch: 'main',
//                     url: 'https://github.com/Vardhangollapalli87/calculator-app.git'
//             }
//         }


//         stage('Build & Test') {
//             steps {
//                 bat 'mvn clean test'
//             }
//         }

//         stage('Package JAR') {
//             steps {
//                 bat 'mvn package'
//             }
//         }

//         stage('Install to Local Repo') {
//             steps {
//                 bat 'mvn install'
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Library JAR packaged and installed successfully'
//             archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
//         }
//         failure {
//             echo 'Build failed'
//         }
//     }
// }

pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout Source Code') {
            steps {
                echo 'Cloning source code from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/Vardhangollapalli87/calculator-app.git'
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Running Maven tests...'
                bat 'mvn clean test'
            }
        }

        stage('Package JAR') {
            steps {
                echo 'Packaging application into JAR...'
                bat 'mvn package'
            }
        }

        stage('Install to Local Maven Repository') {
            steps {
                echo 'Installing JAR into local Maven repository...'
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
        always {
            echo 'Pipeline execution finished'
        }
    }
}

