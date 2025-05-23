pipeline {
    agent { label 'slave-1' }
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/pratikshitch/spring-petclinic-ci-cd'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonar') {
                    sh './mvnw sonar:sonar'
                }
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Docker Build & Push') {
            steps {
                sh 'docker build -t yourdockerhub/petclinic:latest .'
                sh 'docker push yourdockerhub/petclinic:latest'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sshagent(['your-ssh-key-id']) {
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@<App-EC2-IP> "docker pull yourdockerhub/petclinic:latest && docker run -d -p 8080:8080 yourdockerhub/petclinic:latest"'
                }
            }
        }
    }
}
