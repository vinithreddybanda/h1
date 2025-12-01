pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'No build step needed for static HTML.'
            }
        }
        stage('Test') {
            steps {
                script {
                    // Simple check: verify index.html exists
                    if (!fileExists('index.html')) {
                        error('index.html not found!')
                    }
                    echo 'index.html exists.'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'index.html', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy step placeholder. Add deployment scripts here if needed.'
            }
        }
    }
}