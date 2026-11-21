
pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Downloading code from GitHub Staging branch'
                checkout scm
            }
        }

        stage('Python Version') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo 'Executing Calculator Unit Tests'
                sh 'python3 -m unittest -v test_calculator.py'
            }
        }

        stage('Run Calculator') {
            steps {
                echo 'Running Python Calculator'
                sh "printf '10\\n+\\n20\\n' | python3 calculator.py"
            }
        }

    }

    post {
        success {
            echo 'SUCCESS: Python Calculator CI/CD Pipeline Completed!'
        }

        failure {
            echo 'FAILURE: Pipeline Execution Failed!'
        }

        always {
            echo 'Jenkins Pipeline Execution Finished.'
        }
    }
}
