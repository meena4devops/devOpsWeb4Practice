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
                
                
              
               deploy adapters: [tomcat9(credentialsId: '73bad30f-d15b-4d00-ad2c-f8e570d30ea6', path: '', url: '')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
