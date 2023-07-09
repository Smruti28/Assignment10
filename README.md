# Assignment10
8-
pipeline {
    agent any
    tools{
        maven 'Maven' 
    }
    stages {
        stage('Build') {
            steps {
            echo 'Hello World!!!' 
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '7bb6ab7f-34b6-4a38-8400-c7b1cd190439', url: 'https://github.com/MayadeviBhosale/Assignment8_DO.git']])
            }
        }
    }
    post {
            always{
                junit(
                    allowEmptyResults: true, 
                    testResults: '*/test-reports/.xml'
                    )
            } }}
9-
dockerfile
#base image
FROM openjdk:8
COPY . /src/java
RUN ["javac","HelloWorld.java"]
ENTRYPOINT ["java","HelloWorld"]

docker build -t hello-docker-java .
docker images
docker run hello-docker-java
docker tag hello-docker-java smrutiganapa/hello-docker-java
docker login
docker push smrutiganapa/hello-docker-java
docker images
docker pull

10-
