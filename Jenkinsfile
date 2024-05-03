pipeline {
    agent any
    tools {
        nodejs 'yarn'
    }

    stages {
        stage('install') {
            steps {
                sh 'yarn'
            }
        }
        stage('unit tests') {
            steps {
                sh 'yarn test'
            }
            post {
                 always {
                        junit testResults: '**/reports/**/*.xml'
                 }
            }
        }
        stage('build') {
            steps {
                sh 'yarn build'
            }
        }
        stage('integration tests') {
            steps {
                sh 'yarn test:e2e'
            }
            post {
                 always {
                        junit testResults: '**/reports/**/*.xml'
                 }
            }
        }
    }
}

