pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Pull code from your GitHub repository
                git branch: 'main', url: 'https://github.com/dileepkuna111/jenkinsapp.git'
            }
        }
        
        stage('Deploy to Web Server') {
            steps {
                sh '''
                    echo "Deploying HTML files to Nginx web root..."
                    # Clean default files and copy new HTML files
                    sudo rm -rf /usr/share/nginx/html/*
                    sudo cp -r * /usr/share/nginx/html/
                    
                    # Ensure correct permissions for Nginx
                    sudo chmod -R 755 /usr/share/nginx/html
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline executed successfully! Application is live.'
        }
        failure {
            echo 'Pipeline failed. Check configurations.'
        }
    }
}
