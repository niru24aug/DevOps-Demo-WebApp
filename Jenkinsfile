pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                
                echo 'testing pipeline'
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/niru24aug/DevOps-Demo-WebApp.git']]])
            }
            }
        stage('Slack it'){
            steps {
                slackSend channel: '#devops-alerts', 
                          message: 'Hello, world'
            }
        }
    }

        stage('Sonarqube') {
            environment {
                scannerHome = tool 'sonarqubescanner'
            }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh """${scannerHome}/bin/sonar-scanner"""
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }                
         
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }        
        stage('test') {
            steps {
                echo 'testing the application...'
                echo 'test demo the application...'
            }
        }        
    }

