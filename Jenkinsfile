pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                
                echo "This is running on ${readProp['deploy.type']}"
                deploy adapters: [tomcat9(credentialsId: 'ee730b51-1f18-46a2-9e1f-064f6a45feb4', path: '', url: 'http://34.239.102.158:8080/')], contextPath: null, war: '**/*.war'

            }
        }
    }
}
