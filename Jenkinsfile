#!groovy

pipeline {
    agent any

    tools {
        maven "3.6.0" // You need to add a maven with name "3.6.0" in the Global Tools Configuration page
    }

    stages {
        stage("Build") {
            steps {
                sh "ssh -V"
                sh "mvn -version"
                sh "mvn clean install"
                sh "mvn clean compile"
                sh "mvn package"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
                echo "test successful"
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '0ec60cd3-c147-467b-bc23-ceabd7954e28', path: '', url: 'http://localhost:8081/')], contextPath: 'jenkins_calci', onFailure: false, war: '**/*.war'
                echo "Deploy successful";
            }
        }
    }
}
