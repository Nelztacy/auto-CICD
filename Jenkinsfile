pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master', url: 'https://github.com/Nelztacy/auto-CICD.git'
                }
            }
        }
        stage('Publish Artifacts Over SSH') {
            steps {
                script {
                    sshagent(['technel']) {
                        sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/auto/* technel@192.168.197.130:/home/technel/var/www/html'
                    }
                }
            }
        }
    }
}
