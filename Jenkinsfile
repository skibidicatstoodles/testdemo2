pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                // build commands here
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
                // test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying..'
                // deploy commands here
            }
        }
    }

    post {
        // runs after pipeline finishes (success or fail)
        always {
            echo 'Post build condition running'
        }

        // runs only if the build fails
        failure {
            echo 'Post action if build failed'
        }
    }
}
