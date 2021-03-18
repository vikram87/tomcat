pipeline {
    agent any

    stages {
        
		stage('build') {
            steps {
                sh "mvn clean package"
            }
        }
		stage('test') {
            steps {
                sh "mvn test"
            }
        }
		stage('artifact') {
            steps {
                archiveArtifacts artifacts: '**/*war', followSymlinks: false
            }
        }
		
		stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://52.66.30.44:8080')], contextPath: 'test', war: '**/*war'
            }
        }
    }
}
