pipeline {
    agent any

    stages {
        stage('Check Workspace') {
            steps {
                bat 'dir'
            }
        }

        stage('Display sample.txt') {
            steps {
                bat 'type sample.txt'
            }
        }
    }
}
