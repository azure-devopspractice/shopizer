pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
       stage('vcs') {
        steps {
            git url: 'git@github.com:azure-devopspractice/shopizer.git',
                branch: 'develop'
        }
       }
       stage('build') {
        steps {
            sh "mvn clean install"
        }
       }
       stage('Archive artifacts') {
            steps {
                archive includes: '**/target/*.jar'
            }
        }
        stage('Archive JUnit-formatted test results') {
            steps {
                junit testResults: '**/target/surefire-reports/*.xml'
            }
        }
    }
}
