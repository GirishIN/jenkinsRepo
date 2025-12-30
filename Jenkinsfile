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
                sudo cp index.html /var/www/html/index.html
                sudo chown www-data:www-data /var/www/html/index.html
                sudo chmod 644 /var/www/html/index.html
                '''
            }
        }

        stage('Restart Apache') {
            steps {
                sh '''
                sudo systemctl restart apache2
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
