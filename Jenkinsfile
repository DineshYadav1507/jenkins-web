pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -R'
            }
        }

        stage('Validate index.html') {
            steps {
                script {
                    if (!fileExists('index.html')) {
                        error "index.html not found! ❌"
                    } else {
                        echo "index.html found. ✅"
                    }
                }
            }
        }

        stage('Simulated Deploy') {
            steps {
                echo 'Simulating deployment of index.html...'
                // Yaha future me real deploy commands aayengi
                archiveArtifacts artifacts: 'index.html', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Succeeded ✅'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}

