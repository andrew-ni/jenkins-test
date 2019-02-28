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
                sh 'pip install --upgrade pip'
                sh 'pip install -r test-requirements.txt'
                sh 'echo asdfasdf'
            }
        }
        stage('flake8') {
            steps {
                sh 'flake8'
            }
        }
        stage('test') {
            steps {
                sh 'pytest'
            }
        }
    }
}