pipeline {
    agent any
        stages {
        stage('checkout') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/nishchai17/hello-world-war.git'
            }
        }
        stage('build') {
            steps {
                sh 'docker build -t nishchai17/hello-world-war:1.0.1 .'
            }
        } 
         stage('publish') {
            steps {
                withCredentials([usernamePassword(credentialsId: '1207a9ab-d7c7-4b11-a923-b1a116622af2', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                    sh "docker push nishchai17/hello-world-war:1.0.1"
            }
         }  
    }
}
