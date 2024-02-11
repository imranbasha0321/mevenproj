pipeline {
    agent any
    stages {
        stage('continuous download') {
            steps {
                git 'https://github.com/intelliqittrainings/maven.git'
                
            }
        }
        stage('continuous build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('continuous deployment') {
            steps {
                sh 'scp /var/lib/jenkins/workspace/decp/webapp/target/webapp.war ubuntu@172.31.20.131:/var/lib/tomcat9/webapps/mytestapp.war'
            }
        }
        stage('continuous testing') {
            steps {
               git  'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/decp/testing.jar'
            }
        }
        stage('continuous delivery') {
            steps {
                sh 'scp /var/lib/jenkins/workspace/decp/webapp/target/webapp.war ubuntu@172.31.24.202:/var/lib/tomcat9/webapps/myprodapp.war'
            }
        }
        
        
    }
}
