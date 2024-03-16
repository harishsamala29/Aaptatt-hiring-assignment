pipeline {
    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/harishsamala29/Aaptatt-hiring-assignment.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        
        stage('Docker Image') {
            steps {
                sh "docker pull tomcat:9.0"
                sh "docker tag tomcat:9.0 harish78/tomcat:A1"
                sh "docker images"
            }
        }
        
        stage('Docker Run') {
            steps {
                sh "docker stop my_tomcat"
                sh "docker rm my_tomcat"
                sh "docker run -d -p 8081:8080 --name my_tomcat harish78/tomcat:A1"
                sh "docker cp target/sparkjava-hello-world-1.0.war my_tomcat:/usr/local/tomcat/webapps"
                sh "docker ps"
            }
        }
    }
}
