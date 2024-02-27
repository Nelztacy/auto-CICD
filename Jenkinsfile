pipeline {
    stage ('Git Checkout') {
        git 'https://github.com/Nelztacy/auto-CICD.git'
    }

    stage ('Publish Artifacts Over-SSH') {
       steps{
         sshagent(['technel']) {
            sh 'scp -o StrickHostKeyChecking=no /var/lib/jenkins/workspace/auto/* technel@192.168.197.130:/home/technel/var/www/html' 
        }
    }
}
}

