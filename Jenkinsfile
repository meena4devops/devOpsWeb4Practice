pipeline{
    agent any
    tools{
        maven 'Maven'
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
                
                
              
                deploy adapters: [tomcat9(credentialsId: 'ee730b51-1f18-46a2-9e1f-064f6a45feb4', path: '', url: 'http://54.161.190.104:8080/')], contextPath: null, war: '**/*.war'

            }
        }
    }
}
