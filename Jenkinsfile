pipeline {
    agent { 
        docker { 
            image 'python:3.5.1' 
            args '-u root'
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('test') {
            steps {
                sh 'pip install pytest'
                sh 'pytest'
            }
        }
    }
}