pipeline {
    agent any

   tools {
        maven 'maven'

    }
    
    
    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcas', path: '', url: 'http://54.210.249.133:8080/')], contextPath: 'myapp', war: '**/*.war'
            }
        }
    }
}
