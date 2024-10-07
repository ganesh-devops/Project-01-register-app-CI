pipeline {
    agent{ label 'Jenkins-Agent' }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    stages{
        stage("Cleanup Workspace"){
            steps {
                cleanWs()
                }
            }

        stage("checkout form SCM") {
            steps {
               git branch: 'main', credentialsId: 'GitHub', url:'https://github.com/ganesh-devops/Project-01-register-app-CI.git'
            }
        }

        stage("Build Application") {
            steps {
                sh "mvn clean package"
            }
        }

        stage("Build Test") {
            steps {
                sh "mvn Test"
            }
        }

        stage("SonarQube Analysis") {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token') { 
					    sh "mvn sonar:sonar"
                    }
                }
            }
        }

    }
}