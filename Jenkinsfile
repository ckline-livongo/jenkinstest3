pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker --version'
                sh 'touch testfile.txt'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        
    }
    post {
        always {
            archive "testfile.txt"
        }
        success {
            mail to:"ckline@livongo.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body:"Build succeeded"
        }
    }
}
