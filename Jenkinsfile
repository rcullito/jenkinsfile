pipeline {
    agent any 
    stages {
        stage('Setup pipeline') {
            steps {
                script {
                    properties([
                        parameters([
                            string(
                                name: 'deploy_ver',
                                description: 'Version to deploy (if deploy pipeline)'
                            ),
                            choice(
                                name: 'release_level',
                                choices: ['minor', 'major', 'patch'],
                                description: 'Release level (if release pipeline)'
                            )
                        ])
                    ])
                }
            }
        }
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
            }
        }
        stage ('Deploy') {
            steps {
                echo currentBuild.displayName
                echo params.deploy_ver
            }
        }
    }
}
