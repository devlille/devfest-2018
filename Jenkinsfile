pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'npm install'
                dir ('public') { 
                    sh 'bower install'
                }
            }
        }
        stage('deploy') {
            environment {
                FIREBASE_TOKEN = credentials('FIREBASE_TOKEN')
            }
            when {
                branch 'master'
            }
            steps {
                sh './node_modules/firebase-tools/bin/firebase deploy --token $FIREBASE_TOKEN'
            }
        }
    }
}