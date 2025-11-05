pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'echo Building project...'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Running tests...'
            }
        }
    }

    post {
        success {
            echo "Build Successful!"
            emailext(
                to: 'dhruvp3008@gmail.com', 
                subject: "SUCCESS: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build was successful!\nCheck details here: ${env.BUILD_URL}"
            )
        }
        failure {
            echo "Build Failed!"
            emailext(
                to: "dhruvp3008@gmail.com",  
                subject: "FAILURE: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build failed!\nCheck details here: ${env.BUILD_URL}",
                attachLog: true  
            )
        }
    }
}
