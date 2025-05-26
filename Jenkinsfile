pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/tanvi-rm/Practical5_Nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy Application') {
            steps {
                // Kill existing app on port 3000 (optional)
                sh 'fuser -k 3000/tcp || true'

                // Start app in the background
                sh 'nohup npm start > output.log 2>&1 &'
                echo 'App deployed and running at http://localhost:3000'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed.'
        }
    }
}
