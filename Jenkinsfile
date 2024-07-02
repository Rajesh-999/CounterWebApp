pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/Rajesh-999/CounterWebApp.git'
            }
        }
        stage('maven build'){
            steps{
                
                bat '''set MAVEN_HOME=C:\\ProgramData\\chocolatey\\lib\\maven\\apache-maven-3.9.8
                set PATH=%MAVEN_HOME%\\bin;%PATH%
                mvn clean install'''
                
            }	
        }
        stage('deploy to build'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'admin', path: '', url: 'http://51.20.42.183:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
