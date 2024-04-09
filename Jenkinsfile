pipeline{
    agent any
    tools{
        maven 'maven3.96'
    }

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving to Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }


        }
        stage('Deploy to tomcate server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'dev-24', path: '', url: 'http://54.224.147.120:8009/')], contextPath: null, war: '**/*.war'

            }
        }
            
    }
}