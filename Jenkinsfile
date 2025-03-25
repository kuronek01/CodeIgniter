pipeline {
    agent any
    environment {
        CI_ENV = 'testing'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kuronek01/CodeIgniter.git'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'phpunit --configuration application/tests/phpunit.xml'
            }
            post {
                success {
                    echo 'Tests passed successfully!'
                    junit 'application/tests/results/*.xml'
                }
                failure {
                    echo 'Tests failed!'
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
