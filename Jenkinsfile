pipeline{
    agent any
    stages{
        stage("1 Build the image in Docker"){
           steps{
            echo "This is Bulding Image..."
           sh "docker build -t devopsaditya123/python:v1 ."
           }
        }
        stage("2 push the Image in docker Hub"){
            steps{
              withCredentials([usernamePassword(credentialsId: "docker-pass", usernameVariable: "USER" , passwordVariable: "PASS")]){
                      sh "echo $PASS | docker login -u $USER --password-stdin"
                      sh "docker push devopsaditya123/python:v1"
              }
            }
        }
    }
}