pipeline {
    agent any

    tools {
        jdk 'JAVA'
    }

    stages {

        stage('Build Java') {
            steps {
                bat '''
                    echo Compiling Java file...
                    javac Sum.java
                '''
            }
        }

        stage('Execute Java Program') {
            steps {
                bat '''
                    echo Running Java program...
                    java Sum sample.txt
                '''
            }
        }
    }
}
