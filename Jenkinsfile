pipeline {
    agent any

    environment {
        IMAGE_NAME = "static-site:v1"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Push Docker Image (Optional)') {
            steps {
                echo 'Skip or add docker push logic here'
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
