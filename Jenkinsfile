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
    }
}
