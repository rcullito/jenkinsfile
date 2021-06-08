pipeline {
    agent any 
    stages {
        stage('Setup pipeline') {
            steps {
                script {
                    properties([
                        string(
                            name: 'deploy_ver',
                            description: 'Version to deploy (if deploy pipeline)')
                    ])
                }
            }
        }
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
            }
        }
    }
}
