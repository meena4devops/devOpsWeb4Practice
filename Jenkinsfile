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
                
                
                deploy adapters: [tomcat9(credentialsId: 'ff28cb82-63f0-4b2e-9fb3-62dbc6918cc6', path: '', url: 'http://54.161.190.104:8080/')], contextPath: null, war: '**/*.war'

            }
        }
    }
}
