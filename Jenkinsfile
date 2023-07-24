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
                
                
              
               deploy adapters: [tomcat9(credentialsId: '24894b3f-61d7-4206-a0cd-c7bd2599197c', path: '', url: '')], contextPath: null, war: '**/*.war'

            }
        }
    }
}
