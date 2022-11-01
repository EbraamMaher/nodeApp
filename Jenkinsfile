pipeline{

    agent {label 'agent'}
    
    stages{
        stage('Build image'){
            steps{
                withCredentials(usernameColonPassword(credentialsId: 'docker', userVariable: 'USER',passwordVariable: 'PASS')) {
                sh "docker build . -t node-app:$BUILD_TAG"
                sh "docker run -d -p 90:3000 node-app:$BUILD_TAG"
                sh "docker push 852456000/nodejs:$BUILD_TAG"
            }
            
            }
            post {
                success {
                    sh "docker image ls"
                }
                
                }

        }

    }
}
