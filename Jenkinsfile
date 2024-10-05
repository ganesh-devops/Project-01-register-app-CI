pipeline {
    agent{ label 'Jenkins-Agent' }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWS()
            }
        }
        stage('checkout form SCM') {
            steps {
                git branch: 'main', credentials:'GitHub', url:'https://github.com/ganesh-devops/Project-01-register-app-CI.git'
            }
        }
        stage('Build Application') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Build Application') {
            steps {
                sh "mvn Test"
            }
        }
    }
}
