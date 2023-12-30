pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                script {
                    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.40.183.167:8080/')], contextPath: 'muna', war: '**/*.war'
                }
            }
        }
    }
}
