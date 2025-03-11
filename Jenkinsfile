pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Debug') {  // Add this debugging stage
            steps {
                script {
                    sh 'pwd'   // Print current working directory
                    sh 'ls -l' // List all files
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS555 hello.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS555'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'git config --global user.name "PES2UG22CS555"'
                    sh 'git config --global user.email "sinchanachandranaik2004@gmail.com"'
                    sh 'git add hello.cpp'
                    sh 'git commit -m "Added hello.cpp" || echo "No changes to commit"'
                    sh 'git push origin main'
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
            echo "Pipeline failed"
        }
    }
}
