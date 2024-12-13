pipeline {
    agent any
    stages {
        stage('dev build') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Hello world, this is multibranch pipeline for Dev branch'
            }
        }
        stage('feature build') {
            when {
                branch 'feature/*'
            }
            steps {
                echo 'testing Dev...'
            }
        }
        stage('main') {
            when {
                branch 'main'
            }
            steps {
                echo 'deploying Dev...'
            }
        }
    }
} 