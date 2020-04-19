pipeline{
    agent any
    stages{
        
        stage('MavenBuild'){
            steps{
                sh label: '', script: '/opt/maven/bin/mvn clean package'
            }
        }
        stage('Tomcat Deploy'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://10.220.110.123:8080/')], 
            contextPath: null, war: '**/*.war'
            }
        }
    }
    
}
