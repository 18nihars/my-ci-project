pipeline {
    agent any 

    stages {
        stage('Checkout Code') {
            steps {
                // This pulls your latest code from the Git repository
                checkout scm 
                echo 'Source code checked out successfully.'
            }
        }

        stage('Build Environment') {
            steps {
                echo 'Setting up the Python environment...'
                // Jenkins will install the dependencies listed in your requirements.txt
                bat 'pip install -r requirements.txt' 
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running unit tests with pytest...'
                // Jenkins will execute your test file
                bat 'pytest test_app.py'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'SUCCESS: The code built and tested perfectly!'
        }
        failure {
            echo 'FAILURE: A test failed or the build broke. Check the logs above.'
        }
    }
}