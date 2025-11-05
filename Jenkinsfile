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
            mail to: 'Dpatel2297@conestogac.on.ca', 
            from: 'dhruvp3008@gmail.com',
            subject: "SUCCESS: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "The build was successful!\nCheck details here: ${env.BUILD_URL}"
        }
        failure {
            mail to: 'Dpatel2297@conestogac.on.ca', 
            from: 'dhruvp3008@gmail.com',
            subject: "FAILURE: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "The build failed!\nCheck details here: ${env.BUILD_URL}"
        }
    }
}
