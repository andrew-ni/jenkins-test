pipeline {
    agent { 
        docker { 
            image 'python:3.6' 
            args '-u root'
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
                sh 'pip install --upgrade pip'
                sh 'pip install -r test-requirements.txt'
            }
        }
        stage('flake8') {
            steps {
                script {
                    try {
                        echo 'Running flake8...'
                        sh 'flake8 jenkins_test/'
                    } catch(err) {
                        echo 'flake8 validation failed!'
                        currentBuild.result = 'UNSTABLE'
                    }
                }
            }
        }
        stage('test') {
            steps {
                sh 'pytest'
            }
        }
    }
    post {
        always {
            echo 'This will always run after jenkins finishes'
        }
        success {
            echo 'This will run only if successful. no errors during processing. good to archive successful builds'
        }
        failure {
            echo 'This will run only if failed. send feedback to team, via email or slack, requires urgent attention, can be used to rollback to last successful build'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}