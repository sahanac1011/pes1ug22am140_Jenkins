pipeline {
    agent any  // Runs on any available agent
    environment {
        DOCKER_IMAGE = "node:14"
    }
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/sahanac1011/pes1ug22am140_Jenkins.git'
            }
        }
        stage('Install dependencies') {
            agent {
                docker {
                    image 'node:14'
                }
            }
            steps {
                sh 'npm install'
            }
        }
        stage('Build application') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Test application') {
            steps {
                sh 'npm test'
            }
        }
        stage('Push Docker image') {
            steps {
                sh 'docker build -t sahanac1011/pes1ug22am140_Jenkins:$BUILD_NUMBER .'
                sh 'docker push sahanac1011/pes1ug22am140_Jenkins:$BUILD_NUMBER'
            }
        }
    }
}
