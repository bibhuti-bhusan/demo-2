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
		    fileOperations([fileCopyOperation(excludes: '', flattenFiles: false, includes: '*/*.war', targetLocation: '/opt/apache-tomcat/webapps/')])
               }
            }
           }
}
