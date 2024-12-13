pipeline {

    agent {
        node {
            label 'linux'
        }
    }

    options {
        buildDiscarder logRotator( 
            daysToKeepStr: '16', 
            numToKeepStr: '10'
        )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/SabrinaAG-PS/jenkins-2.git']]
                ])
            }
        }

        stage('Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Feature') {
            when {
                branch 'feature/*'
            }
            steps {
                sh """
                echo "Building Artifact for Dev Environment"
                """
                sh """
                echo "Deploying to Dev Environment"
                """
                sh """
                echo "Deploying to QA Environment"
                """
            }
        }

        stage('Deploy To Dev & QA') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact for Dev Environment"
                """
                sh """
                echo "Deploying to Dev Environment"
                """
                sh """
                echo "Deploying to QA Environment"
                """
            }
        }

        stage('Deploy To Staging and Pre-Prod Code') {
            when {
                branch 'main'
            }
            steps {
                sh """
                echo "Building Artifact for Staging and Pre-Prod Environments"
                """
                sh """
                echo "Deploying to Staging Environment"
                """
                sh """
                echo "Deploying to Pre-Prod Environment"
                """
            }
        }

    }   
}
/* pipeline {
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
} */ 