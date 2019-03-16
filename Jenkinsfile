pipeline {
      agent any
	tools{
	    maven 'maven'
	}
	stages {

	   stage ('compile stage') {
	    steps {
		sh 'mvn clean'
		}   
	   }
	   
	   stage ('package stage') {
            steps {
		sh 'mvn package'
                }
           }
	   
	   stage ('install stage') {
            steps {
                sh 'mvn install'
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
