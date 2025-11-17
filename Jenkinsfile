pipeline {
    agent any

    /*
     * Tools section — the name must match what you configured in:
     * Jenkins → Manage Jenkins → Global Tool Configuration → Maven
     */

    /*
     * Parameters: visible when clicking "Build with Parameters"
     */
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version to deploy on prod')
        choice(name: 'CHOOSE_VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Select version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run test stage?')
    }

    /*
     * Global environment variables
     */
    environment {
        NEW_VERSION = '1.3.0'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building Project'
                echo "Using environment variable: ${NEW_VERSION}"
                echo "User-provided VERSION param: ${params.VERSION}"
                echo "Choice selected: ${params.CHOOSE_VERSION}"

                // Example Maven command
                sh "mvn install"
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests }
            }
            steps {
                echo 'Testing Project'
                sh "echo 'Running tests...'"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Project'
                echo "Deploying version ${NEW_VERSION}"
                echo "Deploying user-selected version: ${params.CHOOSE_VERSION}"
            }
        }
    }

    /*
     * Post actions — run after pipeline completes
     */
    post {
        always {
            echo 'Post build condition running'
        }

        failure {
            echo 'Post action triggered because build FAILED'
        }
    }
}
