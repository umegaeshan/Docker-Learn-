pipeline {
    agent any

    stages {
        stage('Deploy to AWS EC2') {
            steps {
                echo 'Connecting to AWS EC2 Server...'
                
                // අර අපි හංගපු .pem කී එක පාවිච්චි කරන්න කියලා Jenkins ට කියනවා
                sshagent(['aws-ec2-key']) {
                    
                    // Windows Jenkins හරහා AWS සර්වර් එකට SSH වී කමාන්ඩ්ස් යැවීම
                    bat """
                        ssh -o StrictHostKeyChecking=no ubuntu@<AWS_PUBLIC_IP> "
                            echo 'Connected to AWS successfully!' &&
                            
                            if [ ! -d 'GrR-ECommerce' ]; then
                                git clone https://github.com/umegaeshan/Docker-Learn-.git GrR-ECommerce
                            fi &&
                            
                            cd GrR-ECommerce &&
                            git pull origin main &&
                            
                            echo 'Building and starting Docker containers on AWS...' &&
                            docker compose down &&
                            docker compose up -d --build
                        "
                    """
                }
            }
        }
    }
}