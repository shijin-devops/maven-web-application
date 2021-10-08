@Library('wallmart-shared') _
pipeline {
    agent any
    options { timestamps () }
    tools {maven 'maven3.6.2'}

    stages {
        stage('GitClone') {
            steps {
                git branch: 'development', url: 'https://github.com/shijin-devops/maven-web-application.git'
            }
        }
        stage('Build') {
            steps {
                build("package")
            }
    }
    
    stage('Deploy') {
            steps {
                sshagent(['1e5d27ab-c6e8-4e68-b885-96f5d1db2430']) {
              sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war centos@3.19.77.179:/opt/apache-tomcat-9.0.53/webapps/ "
}
            }
    }
}
}
