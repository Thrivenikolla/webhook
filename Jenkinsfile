pipeline {
    agent any
    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'branch', value: '$.ref'],
                [key: 'commit_author', value: '$.head_commit.author.name']
            ],
            token: 'your-generic-webhook-token',
            printContributedVariables: true,
            printPostContent: true,
            regexFilterText: '$branch == "refs/heads/main"',
            regexpFilterExpression: 'true',
        )        
    }

    stages {
        stage('Log Webhook Data') {
            steps {
                    echo "Webhook triggered by: ${commit_author}"
                    echo "Branch: ${branch}"
                }
            }
        stage('Build') {
            steps {
                sh 'echo "Building code from branch: ${branch}"'
            }
        }
    }
}
