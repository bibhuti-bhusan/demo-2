pipeline {
      agent any
	tools{
	    maven 'maven'
	}
	stages {
		
           stage ('validate stage') {
            steps {
                sh 'mvn validate'
                }
           }
	   stage ('compile stage') {
            steps {
                sh 'mvn compile'
                }
           }
		
	   stage ('clean stage') {
            steps {
		sh 'mvn clean'
                }
           }
	   
	   stage ('install stage') {
            steps {
                sh 'mvn install'
                }
           }
	   stage ('package stage') {
            steps {
                sh 'mvn package'
                }
           }
	   stage ('deployment stage') {
            steps {
                sh 'mvn deploy'
                }
           }
	   stage ('deployment-to-tomcat') {
            steps {
               sshagent(['tomcat-admin']) {
                sh 'scp -o StrictHostKeyChecking=no  target/*.war root@35.229.70.178:/opt/apache-tomcat/webapps/'
              }
            }
           }

	}
}
