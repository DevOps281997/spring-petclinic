pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'JDK21'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/DevOps281997/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                scp -o StrictHostKeyChecking=no \
                target/*.war \
                ec2-user@34.201.167.174:/opt/tomcat/webapps/
                '''
            }
        }

    }
}
