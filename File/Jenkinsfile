pipeline {
    agent any
    tools{
        maven 'maven-3.8.5'
    }
    stages{
        stage("Checkout the project") {
           steps{
               git branch: 'master', url: 'https://github.com/ranvivekjan/springboot-maven-nexus-deploy2.git'
           } 
        }
        stage("Build the package"){
            steps {
                sh 'mvn clean package'
            }
        }
        stage("Sonar Quality Check"){
		steps{
		    script{
		     withSonarQubeEnv(installationName: 'sonar-9', credentialsId: 'jenkins-sonar-token') {
		     sh 'mvn sonar:sonar'
	    	}
		    }
		}
        }
    }
}
