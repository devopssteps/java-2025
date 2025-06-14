pipeline {
    agent {
        node {
            label "maven"
        }
    }


    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/devopssteps/java-2025.git'
            }
        }
    }
}

