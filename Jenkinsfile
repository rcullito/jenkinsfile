GString commitAtTag(String tag) {
    return sh(returnStatus: true, script: "git rev-list -n 1 ${tag}").trim()
}

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
                echo 'Tagged Sha is:'
                echo commitAtTag(params.deploy_ver)
            }
        }
    }
}
