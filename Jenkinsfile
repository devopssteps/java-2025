pipeline {
    agent {
        node {
            label "maven"
        }
    }
    environment {
        PATH = "/opt/maven/bin:$PATH"
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
    }
}

