pipeline {
    agent any
    tools {
        localMaven 'Maven 3.6.3'
    }
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Create Tomcat Docker Image'){
            steps {
                sh "pwd"
                sh "ls -a"
                sh "docker build -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}