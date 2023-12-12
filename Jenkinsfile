pipeline {
    agent any
    environment{
        DOCKERHUB_ENV= credentials('menna-jenkins')
    }
    stages {
        stage('CI') {
            steps {
                
               sh "docker login -u mennahg --password-stdin"  //pass unencrypted
               sh "docker build -f dockerfile -t mennahg/nodeapp:v1"
               sh "docker push mennahg/nodeapp:v1"
            }
        }

        stage('CD') {
            steps {
                sh "docker login -u mennahg --password-stdin"  //pass unencrypted
                sh "docker run -d -p 3000:3000 mennahg/nodeapp:v1"
            }
        }

        
    }
}
