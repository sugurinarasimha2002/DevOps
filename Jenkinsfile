
pipeline {
    agent any

    stages {

        // 1. Checkout source code from GitHub
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sugurinarasimha2002/DevOps.git'
            }
        }

        // 2. Check project files
        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        // 3. Build Maven project
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        // 4. Analyze code using SonarQube
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                        mvn org.sonarsource.scanner.maven:sonar-maven-plugin:sonar ^
                        -Dsonar.projectKey=test_project
                    '''
                }
            }
        }

        // 5. Artifactory stage
        stage('Artifactory') {
            steps {
                echo 'Artifactory stage: configure artifact upload here.'
                bat 'dir target'
            }
        }

        // 6. Monitoring stage
        stage('monitoring') {
            steps {
                echo 'Monitoring stage: configure monitoring integration here.'
            }
        }
    }

    post {
        success {
            echo 'Build, SonarQube analysis, and configured stages completed successfully!'
        }

        failure {
            echo 'Build failed. Check the Jenkins Console Output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
