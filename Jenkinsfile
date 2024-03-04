pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments') {
            parallel {
                stage ("Deploy to Staging") {
                    steps {
                        sh "scp -v -o StrictHostKeyChecking=no **/*.war technel@192.168.197.130:/home/technel/var/www/html"
                    }
                }
            }
        }
    }
}
