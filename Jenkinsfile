pipeline{
    agent any
    stages{
        stage('checkout the code')
        {
            steps{
                checkout scm
            }
        }
        stage("build docker image"){
            steps{
                sh 'docker build -t Automate-Docker-Build-image:v1 . '
            }
        }
        stage("Push docker image"){
            steps{
                withCredentials([string(credentialsId: 'DockerPwd', variable: 'DockerPwd')]) {
                    sh 'docker login -u sitaramu2003 -p ${DockerPwd}'
                    sh 'docker tag Automate-Docker-Build-image:v1 sitaramu2003/Node-js-app:1.0'
                    sh 'docker push sitaramu2003/Node-js-app:1.0'
                    sh 'docker logout'
}
                }

            }
        }

}
