pipeline{
    agent{
        label 'Agent_01'
    }

    stages{

        stage("Git Checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/VaiPandey/demo-counter-app.git'
            }
        }

        stage("Unit Test"){
            steps{
                bat 'mvn test'
            }
        }

        stage("Integration Test"){
            steps{
                bat 'mvn verify -DskipUnitTests'
            }
        }

        stage("Buiding"){
            steps{
                bat 'mvn clean install'
            }
        }

        stage("Code Analysis"){
            steps{
                script{
                    withSonarQubeEnv(installationName: 'Sonar_Scanner',credentialsId: 'Sonar_Authy') {
                        bat 'mvn clean package sonar:sonar'
                    }
                }
            }
        }

        stage("Nexus Upload"){
    steps{
        script{
            nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], 
            credentialsId: 'nexus_authy', 
            groupId: 'com.example', 
            nexusUrl: '192.168.1.12:8081', 
            nexusVersion: 'nexus2', 
            protocol: 'http', 
            repository: 'springboot-repo', 
            version: '1.0.0'
        }
    }
}
        
    }
}
