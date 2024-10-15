pipeline{
    agent {label 'Jenkins-Agent'}
    tools{
        jdk 'Java17'
        maven 'Maven3'
    }
    stages{
        stage('Cleanup Workspace'){
            steps {
                cleanWs
            }
        }
            
        stage('Checkout for SCM'){
            steps {
                git branch:'main', credentialsId:'GitHub', URL:'https://github.com/ganesh-devops/Project-01-register-app-CI.git'
            }
        }

        stage('Build Application'){
            steps{
                sh "mvn clean package"
            }
        }

      
    }

}