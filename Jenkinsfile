pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-auth-ssh', url: 'git@github.com:Hectopascal7/web_demo.git']]])
            }
        }
        stage('Build Project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Publish Project') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-auth', path: '', url: 'http://sincerely.org.cn:8888/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
