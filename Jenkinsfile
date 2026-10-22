pipeline {
    agent any
      stages{
        stage("this is Testing Phase"){
           steps{
              echo " scnanning code for Bugs and Vulnerabilities"
              withSonarQubeEnv("SonarQube"){
                sh '''
                sonar-scanner \
                      -Dsonar.projectKey=my-python-project \
                      -Dsonar.sources=. \
                      -Dsonar.host.url=http://34.226.197.185:9000 \
                      -Dsonar.login=sqa_4202215858d710d2845cba76489b5afc76812ec7
                      
                    '''
                     }
                     echo "SonarQube Scan pass"
           }
        }
        stage("2 Build the image for Docker"){
            steps{
                 echo "Docker Building Proces........."
                sh "docker build -t devopsaditya123/py:v1 . "
            }
        }
        stage("3 Push the Docker Hub"){
            steps{
                withCredentials([usernamePassword(credentialsId: "docker-pass", usernameVariable : "USER", usernamePassword: "PASS")]){
                      sh "echo $PASS | docker login -u $PASS --password-stdin"
                      sh "docker push devopsaditya123/py:v1"
                }
            }
        }
      }
}