pipeline {
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
}
    stages {
        stage("git") {
            steps{
            git credentialsId: 'github_cred', url: 'https://github.com/anandsukan007/maven-project.git'
            }
        }
        stage("build code") {
            steps{
            sh "mvn clean package"
            }
        }
        stage("Deply-dev") {
            agent { label 'slave_kubemaster' }
            steps{
            sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ananddevops2021@10.128.0.7:/opt/apache-tomcat-8.5.61/webapps"
}
            }
        }
    }

 
