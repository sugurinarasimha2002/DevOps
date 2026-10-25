
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sugurinarasimha2002/DevOps.git'
            }
        }

        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('codequality') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Artifactory') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('monitoring') {
            steps {
                bat 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Check the console output.'
        }
    }
}
