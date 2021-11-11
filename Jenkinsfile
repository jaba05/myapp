pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'war', url: 'https://github.com/jaba05/myapp.git'
            }
        }
		stage('Build') {
            steps {
                bat 'mvn clean'
				bat 'mvn install'
            }
        }
		stage('Deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'warserver', path: '', url: 'http://localhost:8080/')], contextPath: 'newproject-war', war: '**/*.war'
            }
        }
    }
}
