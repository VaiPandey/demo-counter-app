pipeline{
    agent{
        label Agent_01
    }

    stages{

        stage("Git Checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/VaiPandey/demo-counter-app.git'
            }
        }
    }
}