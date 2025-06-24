pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp:v1"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/user/docker-ansible-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Push Docker Image (Optional)') {
            steps {
                echo 'You can push to Docker Hub or ECR here'
                // sh 'docker push yourrepo/$IMAGE_NAME'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                ansiblePlaybook(
                    playbook: 'ansible/deploy.yml',
                    inventory: 'ansible/inventory.ini',
                    credentialsId: 'my-ssh-key-id'
                )
            }
        }
    }
}
