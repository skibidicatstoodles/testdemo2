pipeline {
    agent any

    environment {
        // Global environment variable accessible in any stage
        NEW_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Building version ${NEW_VERSION}"
                // build commands here
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
                echo "Testing version ${NEW_VERSION}"
                // test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying..'
                echo "Deploying version ${NEW_VERSION}"
                // deploy commands here
            }
        }
    }

    post {
        // Always executed at the end
        always {
            echo 'Post build condition running'
        }

        // Only if pipeline fails
        failure {
            echo 'Post action if build failed'
        }
    }
}
