pipeline {
    agent any
    options {
        timestamps()
    }    
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
                sh 'cat files.txt'
            }
        }
        
    }
    post {
        always {
            archive "testfile.txt"
        }
        success {
            mail to:"ckline@livongo.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body:"Build succeeded"
            hipchatSend room: "Curtis_Test", message: "Build Complete: ${env.JOB_NAME} build #${env.BUILD_NUMBER}"
        }
        failure {
            hipchatSend room: "Curtis_Test", message: "Build FAILED: ${env.JOB_NAME} build #${env.BUILD_NUMBER}"
        }    
    }
}
