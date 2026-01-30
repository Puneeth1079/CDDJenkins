pipeline {
    agent any

    options {
        timestamps()
    }

    environment {
        // Change this to your repo URL
        REPO_URL = 'https://github.com/Puneeth1079/CDDJenkins.git'
        // If your default branch is main, keep 'main'. Otherwise use 'master' or your branch name.
        BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                // If repo is public, this works directly.
                // For private repos, use Jenkins credentials (see note below).
                git branch: "${env.BRANCH}", url: "${env.REPO_URL}"
            }
        }

        stage('Verify file') {
            steps {
                script {
                    if (!fileExists('sample.txt')) {
                        error "sample.txt not found in workspace. Check repo root path or branch."
                    }
                }
                echo "✅ sample.txt found"
            }
        }

        stage('Read and Print sample.txt') {
            steps {
                sh '''
                    echo "----- sample.txt content -----"
                    cat sample.txt
                    echo "------------------------------"
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'sample.txt', fingerprint: true
            }
        }
    }

    post {
        always {
            echo "Build finished. Cleaning workspace..."
            cleanWs()
        }
    }
}
