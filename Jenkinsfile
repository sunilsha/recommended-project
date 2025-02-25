pipeline {
    agent any
    //triggers {
    //    upstream(upstreamProjects: "poc-pre-build-job", threshold: hudson.model.Result.SUCCESS)
    //}    
    stages {
        stage('Generate Pre-Signed URL') {
            steps {
                script {
                    // Trigger the 'Generate Pre-Signed URL' job
                    def artifactLocationBuild = build(
                        job: 'poc-pre-build-job', // Full path if within folders, e.g., 'Folder/Generate_Pre-Signed_URL_Job'
                        wait: true // Waits for the completion of the triggered job
                    )
                    echo "Result: ${artifactLocationBuild.result}"
                    echo "=== RunWrapper Object Properties ==="
                    artifactLocationBuild.metaClass.properties.each { property ->
                        echo "${property.name}: ${artifactLocationBuild[property.name]}"
                    }                    
                    //PRESIGNED_URL = readFile('presigned_url.txt').trim()
                }
            }
        }
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
                sh 'for ((i=1; i<=10; i++)); do echo "Executing step $i"; sleep 2; done'
                echo 'Build stage: finished build.'
            }
        }
        stage('Deploy') {
            steps {
                build 'poc-deploy-drupal-code'
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
