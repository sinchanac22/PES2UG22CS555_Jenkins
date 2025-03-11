
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Intentional Error: Typo in 'g++' command or invalid file
                    sh 'g++ -o PES2UG22CS555-1 hello.cp' // Error: wrong file extension
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS555-1'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'git config --global user.name "PES2UG22CS555"'
                    sh 'git config --global user.email "sinchanachandranaik2004@gmail.com"'
                    sh 'git checkout -B main origin/main'
                    sh 'git add -A'
                    sh 'git commit -m "Added hello.cpp file" || echo "No changes to commit"'
                }
            }
        }

        stage('Post Actions') {
            steps {
                echo "Pipeline completed successfully"
            }
        }
    }

    post {
        success {
            echo "Build and deployment successful!"
        }
        failure {
            echo "Pipeline failed" // ✅ Should trigger after the intentional error
        }
    }
}
