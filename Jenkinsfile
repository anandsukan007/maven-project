pipeline {
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
}
    stages {
        stage("git") {
            steps{
            git credentialsId: 'github_cred', url: 'https://github.com/jleetutorial/maven-project.git'
            }
        }
        stage("build code") {
            steps{
            sh "mvn clean install"
            }
        }
        stage("Deply-dev") {
            when { anyof { branch 'master'}
            steps{
            sshagent(['slave_dev']) {
       sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ananddevops2021@10.128.0.7:/opt/apache-tomcat-8.5.61/webapps"
}
            }
        }
    }
}
 
