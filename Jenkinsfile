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
        
    }
}