pipeline {
    agent {
        node {
            label "maven"
        }
    }
    environment {
        PATH = "/opt/maven/bin:$PATH"
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-credential1')
    }

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/devopssteps/java-2025.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker build -t devopssteps/myapp:latest .'
            }
        }
        stage('docker login and push image to docker hub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push devopssteps/myapp:latest'
            }
        }
    }
}

