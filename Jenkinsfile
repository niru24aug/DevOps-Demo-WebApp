pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/niru24aug/DevOps-Demo-WebApp.git']]])
            }
        }
         
        stage('build') {
            steps {
                echo 'building the applicaiton...'
                echo 'Demo the applicaiton...'
            }
        }        
        stage('test') {
            steps {
                echo 'testing the application...'
                echo 'test demo the application...'
            }
        }        
    }
}
