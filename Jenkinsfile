pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/GirishIN/jenkinsRepo.git' 
            }
        }
 

        stage('Deploy HTML') {
            steps {
                sh '''
                cp index.html /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment successful! Open browser and access server IP."
        }
        failure {
            echo "❌ Deployment failed. Check Jenkins logs."
        }
    }
}
