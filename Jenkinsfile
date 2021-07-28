#! groovy
pipeline {
    agent any

    tools {
        gradle "gradle"
    }
    stages {
        stage('Check Gradle Version') {
            steps {
                sh 'gradle --version'
                echo "added small change old"
            }
        }
        stage('Build Gradle') {
            steps {
                sh 'gradle build'
            }
        }
        stage('Copy to dev server'){
            steps{
                echo 'copy file to remote server'
                sshagent(['remote-server']){
                    sh 'scp build/libs/pipeline_job.jar remote@192.168.50.34:/home/remote/'
                }
            }
        }
    }
}