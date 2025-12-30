pipeline {
    agent any 

    environment {
        APP_NAME = "Smart Toy Store"
        TEST_REPORT = "results.xml"
    }

    stages {
        stage('Install') {
            steps {
                echo "--- Starting Stage: Install for ${env.APP_NAME} ---"
                sh 'pip install pytest' 
            }
        }

        stage('Test') {
            steps {
                echo "Running automation tests..."
                sh "pytest --junitxml=${env.TEST_REPORT}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the toy store updates to production..."
                sh 'echo "Deployment successful!"'
            }
        }
    }

    post {
        always {
            junit "${env.TEST_REPORT}" 
            echo "Pipeline finished. Cleaning up..."
        }
        success {
            echo "Success! All toys are safe and ready for the store." [cite: 60]
        }
        failure {
            echo "Alert! The tests failed. Check the logs." [cite: 60]
        }
    }
}
