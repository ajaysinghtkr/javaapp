pipeline {
    agent any

    tools {
        // Specify the Maven version you have configured in Jenkins
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/ajaysinghtkr/javaapp.git'
            }
        }

        stage('Build') {
            steps {
                // Navigate to the directory containing the POM file, if needed
                dir('javaapp') {
                    // Run Maven build
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                // Navigate to the directory containing the POM file, if needed
                dir('javaapp') {
                    // Run tests with Maven
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main' // Deploy only from the main branch
            }
            steps {
                // Example deploy step
                echo 'Deploying application...'
                // Add your deployment commands here, e.g., scp, rsync, etc.
                // sh 'deploy.sh'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
        always {
            echo 'Cleaning up...'
            // Add any cleanup tasks if necessary
        }
    }
}
