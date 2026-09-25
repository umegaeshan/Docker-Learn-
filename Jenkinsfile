pipeline {
    agent any

    stages {
        stage('Deploy to AWS EC2') {
            steps {
                echo 'Connecting to AWS EC2 Server...'
                
                sshagent(['aws-ec2-key']) {
                    
                    // Windows CMD සඳහා සියලුම SSH විධානයන් එකම පේළියකට ගෙන ඇත
                    bat """
                        ssh -o StrictHostKeyChecking=no ubuntu@13.60.53.69 "echo 'Connected to AWS successfully!' && if [ ! -d 'GrR-ECommerce' ]; then git clone https://github.com/umegaeshan/Docker-Learn-.git GrR-ECommerce; fi && cd GrR-ECommerce && git pull origin main && docker compose down && docker compose up -d --build"
                    """
                }
            }
        }
    }
}