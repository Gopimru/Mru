pipeline {
    agent any

    stages {

        // 1️⃣ Checkout
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/example/myapp.git'
            }
        }

        // 2️⃣ Build
        stage('Build') {
            steps {
                sh '''
                python -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        // 3️⃣ Test
        stage('Test') {
            steps {
                sh '''
                source venv/bin/activate
                pytest tests/
                '''
            }
        }

        // 4️⃣ Deploy
        stage('Deploy') {
            steps {
                sh '''
                source venv/bin/activate
                scp -r ./myapp user@server:/var/www/myapp
                ssh user@server "systemctl restart myapp"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully on master!"
        }
        failure {
            echo "Pipeline failed. Check logs."
        }
    }
}
