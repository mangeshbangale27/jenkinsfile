pipeline{
    agent any
    tools{
        maven "maven"
    }
    stages{
        stage("checkout scm"){
            steps{
                git branch: 'main', url: 'https://github.com/mangeshbangale27/login.git'
            }
        }
        stage("build"){
            steps{
                sh "mvn clean install"
            }
        }
    
        stage ('Server'){
            steps {
               rtServer (
                 id: "jfrog",
                 url: 'http://52.66.51.106:8082//artifactory',
                 username: 'admin',
                  password: 'P@ssword12345',
                  bypassProxy: true,
                   timeout: 300
                        )
            }
        }
        stage('Upload'){
            steps{
                rtUpload (
                 serverId:"jfrog" ,
                  spec: '''{
                   "files": [
                      {
                      "pattern": "*.war",
                      "target": "maven-repo-1"
                      }
                            ]
                           }''',
                        )
            }
        }
        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "jfrog"
                )
            }
        }
        
    }
}
