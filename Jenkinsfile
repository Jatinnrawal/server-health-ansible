pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate Ansible') {
            steps {
                sh 'ansible-playbook -i inventory setup.yml --syntax-check'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook -i inventory setup.yml'
            }
        }

        stage('Verify Website') {
            steps {
                sh 'curl -f http://localhost'
            }
        }
    }
}
