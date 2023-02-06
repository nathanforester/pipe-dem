pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
		    }
    stages {
        stage('update apt cache') {
            steps {
                sh 'sudo apt update'
            }
        }
        stage('install apache') {
            steps {
                sh 'sudo apt install nginx -y'
            }
        }

        stage('connect via ssh deploy server') {
            steps {
                sh '''
                      ssh -i /home/ubuntu/.ssh/myKey -o StrictHostKeyChecking=no ubuntu@3.9.29.51 << EOF
                      sudo touch /home/ubuntu/readme
                      sudo echo "hello" > /home/ubuntu/readme
                      EOF
                   '''
            }
        }
    }
}
