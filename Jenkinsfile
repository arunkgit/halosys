currentBuild="projectName#id"

pipeline{
    agent any
    
    environment {
        BUILD = 'Maven Build success'
        DEPLOY = 'Deploying artifacts success'
    }
    
    stages{
       stage('MavenBuild'){
            steps{
                sh label: '', script: '/opt/maven/bin/mvn clean package xy'
                echo "${env.BUILD}"
            }
        }
        stage('Tomcat Deploy'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://10.220.110.123:8080/')], 
            contextPath: null, war: '**/*.war'
                echo "${env.DEPLOY}"
            }
        }
    }
    
    post {
	  failure {
	    mail body: "Please go to ${BUILD_URL} and verify the build",
		 subject: "Job ${JOB_NAME}##${BUILD_NUMBER} is failed", 
	    	 to: 'myowngithub@gmail.com'
	  }
	}
    
}
