pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS= credentials('menna-jenkins')
    }
    stages {
        stage('CI') {
            steps {

               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u mennahg --password-stdin"
               sh "pwd"
               sh "docker build -f dockerfile -t mennahg/nodeapp:v1 ."
               sh "docker push mennahg/nodeapp:v1"
                }
            }
        

        stage('CD') {
            steps {
               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u mennahg --password-stdin"
               sh "docker run -d -p 3000:3000 mennahg/nodeapp:v1"
            }
        }
    }
        
    }
