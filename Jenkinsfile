pipeline {
    agent any
    environment {
        // Install the Maven version configured as "M3" and add it to the path.
        //maven "M3"
        mvnHome = tool name: 'MyMaven', type: 'maven'
    }
    
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/neelam15/sample-maven.git'

                // Run Maven on a Unix agent.
                //sh "mvn -Dmaven.test.failure.ignore=true clean package"
                sh "${mvnHome}/bin/mvn clean package"

            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
