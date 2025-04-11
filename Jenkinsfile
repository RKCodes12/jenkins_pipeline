pipeline {
    agent any
    
    tools {
        // Tools configuration
        maven 'Maven_S3'
        jdk 'java_S3'
    }

    stages {
        stage('Fetch code') {
            // Fetch code from VCM (GitHub)
            steps {
                echo 'fetching code form my github account'
                git branch: 'main', url: 'https://github.com/RKCodes12/jenkins_pipeline.git'
            }
        }

        stage('Build') {
            // Build
            steps {
                sh 'mvn clean install -DskipTests'
            }

            post {
                // Post build actions, Archive, Notifications
                success {
                    echo 'Now Archiving it...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Unit Test') {
            // Performing unit tests
            steps {
                echo 'Running unit tests...'
                // Add your test commands here
            }
        }
    }
}
