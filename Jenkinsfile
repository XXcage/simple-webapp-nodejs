# webapp-nodejs
Sample Web Application Written in Node.js
Jenkins Pipeline:

pipeline {
    agent any
    stages {
        stage('Initialize') {
            steps {
                cleanWs()
            }
        }
        stage('SCM Checkout') {
            steps {
                git 'https://github.com/XXcage/simple-webapp-nodejs.git'
            }
        }
        stage('Install') {
            steps {
                nodejs('node8') {
                    script {
                        if (isUnix()) {
                            sh "npm install"
                        }
                        else {
                            bat "npm install"
                        }
                    }
                }
            }
        }
        stage('Test') {
            steps {
                nodejs('node8') {
                    sh "npm run test"
                }
            }
        }
        stage('Deploy-Test-Env') {
            steps {
                sh "npm run start"
                sleep(60)
            }
        }
    }
}
