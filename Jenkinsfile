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
            }
        }
        stage("deploy") {
            steps {
                
            }
        }
    }
}
