pipeline{
    agent any
    stages{
        stage('checkout the code')
        {
            steps{
                checkout scm
            }
        }
        stage('Test'){
            steps{
                sh 'npm install'
                sh 'npm test'
            }
        }
        stage('Build'){
            steps{
                sh 'npm run build'
            }
        }
        stage("build docker image"){
            steps{
                script{
                    sh 'docker build -t Automate-Docker-Build-image:v1 . '
                }
            }
        }
        stage("Push docker image"){
            steps{
                withCredentials([string(credentialsId: 'DockerPwd', variable: 'DockerPwd')]) {
                    sh 'docker login -u sitaramu2003 -p ${DockerPwd}'
                    sh 'docker tag Automate-Docker-Build-image:v1 sitaramu2003/Node-js-app:1.0'
                    sh 'docker push sitaramu/Node-js-app:1.0'
                    sh 'docker logout'
}
                }

            }
        }

}
