def taggedCommit = null
def branchTriggered = null 

Boolean validTag(String tag) {
    return sh(returnStatus: true, script: "git rev-list -n 1 ${tag}") == 0
}

GString commitAtTag(String tag) {
    return sh(returnStdout: true, script: "git rev-list -n 1 ${tag}").trim()
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
                    taggedCommit = validTag(params.deploy_ver) ? commitAtTag(params.deploy_ver) : null
                    branchTriggered = currentBuild.getBuildCauses('jenkins.branch.BranchEventCause')
                }
            }
        }
        stage('Log Build Information') {
            steps {
                echo 'Branch Triggered is:'
                echo branchTriggered
            }
        }
        stage ('Deploy') {
            when {
                expression { return taggedCommit != null}
            }
            steps {
                echo currentBuild.displayName
                echo params.deploy_ver
                echo 'Tagged Sha is:'
                echo taggedCommit
            }
        }
    }
}
