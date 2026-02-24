pipeline {
    agent any

    tools {
    maven 'maven'
    jdk 'jdk-21'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/Divine-Marshal/my-web-app'
                 
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'my-webapp',
                war: 'target/my-webapp.war'
            }
        }
    }
}
