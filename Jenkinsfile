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
                sh 'mvn clean package'
            }
        }
 stage('Push artifacts into artifactory') {
            steps {
              rtUpload (
                serverId: 'JFROG',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.war",
                          "target": "example-repo-local/"
                        }
                    ]
                }'''
              )
	      }
	   }

    }
}
