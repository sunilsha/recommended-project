pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/drupal/recommended-project.git'
            }
        }

        stage('Install') {
            steps {
                echo 'Install stage: start'
                //sh 'which php'
                sh 'for ((i=1; i<=50; i++)); do echo "Executing step $i"; sleep 1; done'
                echo 'Install stage: finshed'
                //sh 'curl -sS https://getcomposer.org/installer | php'
                //sh 'php composer.phar install'
            }
        }

        stage('Test') {
            steps {
                // Run Drupal tests or other testing framework as needed
                echo 'Test stage: running unit tests'
                sh 'for ((i=1; i<=10; i++)); do echo "Executing step $i"; sleep 2; done'
                echo 'Test stage: finished running unit tests'
            }
        }
        
        stage('Build') {
            steps {
                // Your build steps
                echo 'Build stage: running build.'
                sh 'for ((i=1; i<=10; i++)); do echo "...................."; sleep 2; done'
                echo 'Build stage: finished build.'

            }
        }
    }

    post {
        success {
            echo 'Build and tests successful.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
