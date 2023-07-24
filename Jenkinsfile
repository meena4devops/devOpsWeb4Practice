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
                
                
              
               deploy adapters: [tomcat9(credentialsId: '9ac4a79f-8f23-4010-a902-b2dce48e0675', path: '', url: '')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
