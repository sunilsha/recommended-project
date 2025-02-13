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
                sh 'which php'
                sh 'sleep 10'
                echo 'Install stage: finshed'
                //sh 'curl -sS https://getcomposer.org/installer | php'
                //sh 'php composer.phar install'
            }
        }

        stage('Test') {
            steps {
                // Run Drupal tests or other testing framework as needed
                echo 'Test stage: running unit tests'
                sh 'sleep 10'
                echo 'Test stage: finished running unit tests'
            }
        }
        
        stage('Build') {
            steps {
                // Your build steps
                echo 'Build stage: running build.'
                sh 'sleep 10'
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
