pipeline{
	agent any

	stages{
	
		stage ('Checkout'){

			steps {
					checkout scm
			}
		}
		

		stage ('Build'){

			steps {
					withMaven(maven : 'maven'){
						sh 'mvn install'
				}
			}
		}

		stage ('Test'){
		
			steps{
					withMaven(maven : 'maven'){
						sh 'mvn test'
				}
			}
		}
		
		stage ('Tomcat Deploy'){
		  
      sshagent(['423b5b58-c0a3-42aa-af6e-f0affe1bad0c']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war  centos@18.220.105.79:/usr/share/tomcat/webapps/" 
  }
		}
		
	}
}
