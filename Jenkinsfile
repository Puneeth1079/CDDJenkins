pipeline {
    agent any

    tools {
        // Make sure JDK is configured in Jenkins (Global Tool Configuration)
        jdk 'JDK21'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Puneeth1079/CDDJenkins.git'
            }
        }

        stage('Verify Files') {
            steps {
                script {
                    if (!fileExists('hello.jar')) {
                        error "hello.jar not found"
                    }
                    if (!fileExists('sample.txt')) {
                        error "sample.txt not found"
                    }
                }
            }
        }

        stage('Run Java Program') {
            steps {
                sh '''
                    echo "Running Java application..."
                    java -jar hello.jar sample.txt
                '''
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
