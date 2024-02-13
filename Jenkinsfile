pipeline{
    agent any

    stages{
        stage ('Build'){
             steps{
                sh 'mvn clean package'
             }
             post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts Artifacts: '**/target/*.war'
                }
             }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'ff5a60df-c693-44de-835d-799c61559e2a', path: '', url: 'http://localhost:2525/')], contextPath: null, war: '**/*.war'
            }
        }
        }
    }
