pipeline {
    agent any
    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'branch', value: '$.ref'],
                [key: 'commit_author', value: '$.head_commit.author.name']
            ],
            token: '9876543210',
            printContributedVariables: true,
            printPostContent: true,
            regexpFilterText: '$branch',
            regexpFilterExpression: '^refs/heads/main$',
        )        
    }

    stages {
        stage('Log Webhook Data') {
            steps {
                script {
                    echo "Webhook triggered by: ${env.commit_author ?: 'N/A'}"
                    echo "Branch: ${env.branch ?: 'N/A'}"
                    }
                }
            }
        stage('Build') {
            steps {
                bat 'echo "Building code from branch: ${branch}"'
            }
        }
    }
}

// This Jenkinsfile uses the Generic Webhook Trigger plugin to listen for GitHub webhook events.