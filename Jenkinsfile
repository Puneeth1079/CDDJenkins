pipeline {
    agent any

    tools {
        // Use the JDK tool name that exists in your Jenkins (you said it's "JAVA")
        jdk 'JAVA'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Puneeth1079/CDDJenkins.git'
            }
        }

        stage('List Files') {
            steps {
                bat '''
                    echo ==== Workspace Files ====
                    dir
                    echo =========================
                '''
            }
        }

        stage('Verify Files') {
            steps {
                script {
                    if (!fileExists('hello.java')) error "hello.java not found"
                    if (!fileExists('sample.txt')) error "sample.txt not found"
                }
                echo "✅ Files found"
            }
        }

        stage('Compile') {
            steps {
                bat '''
                    echo Compiling hello.java...
                    javac -version
                    javac hello.java
                    echo After compile:
                    dir
                '''
            }
        }

        stage('Run Java Program') {
            steps {
                bat '''
                    echo Running program...
                    java -version
                    java hello sample.txt
                '''
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/*.class, sample.txt', fingerprint: true
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
