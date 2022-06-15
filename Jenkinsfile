pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker_hub')
    }
    stages{
        stage("build a code"){
            steps{
                script{
                    sh "mvn clean install"
                }
            }
        }
         stage("build a image"){
            steps{
                script{
                    sh "docker build -t kallepalli/mynewimage:$BUILD_NUMBER ."
                }
            }
        }
        stage("push a image"){
            steps{
                script{
                    withCredentials([usernameColonPassword(credentialsId: 'docker_hub', variable: 'docker_hubc')]) {
 
                        }
                    sh "docker login -u kallepalli -p ${docker_hubc}"
                    
                    sh "docker push kallepalli/mynewimage:$BUILD_NUMBER"
                }
            }
        }
    }
}