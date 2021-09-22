pipeline {
    agent any
    stages {
        stage('Build') {
                // Get some code from a GitHub repository
                git 'https://github.com/neelam15/sample-maven.git'
                def mvnHome = tool name: 'MyMaven', type: 'maven'
                sh "${mvnHome}/bin/mvn clean package"
                // Run Maven on a Unix agent.
                //sh "mvn -Dmaven.test.failure.ignore=true clean package"
        }
    }
}
