pipeline {
    agent any

    environment {
        BUILD_DIR = 'build'
    }

    stages {
        stage('Clone Repository') {
            steps { 
                git branch: 'main', url: 'https://github.com/sahanac1011/pes1ug22am140_Jenkins.git'
            }
        }
        stage('Setup') {
            steps {
                echo 'Setting up environment...'
                sh 'mkdir -p $BUILD_DIR'
            }
        }
        stage('Parallel Tasks') {
            parallel {
                stage('Build') {
                    steps {
                        echo 'Compiling source code...'
                        sh 'g++ -o $BUILD_DIR/hello_exec main/hello.cpp'
                    }
                }
                stage('Test') {
                    steps {
                        echo 'Running unit tests...'
                        sh './$BUILD_DIR/hello_exec'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'echo "Simulated deployment step"'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline encountered an error!'
        }
    }
}
