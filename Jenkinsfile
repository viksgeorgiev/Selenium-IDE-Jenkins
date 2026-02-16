pipeline{
    agent any
    stages{
        stage("Checkout code"){
            steps{
                git branch: 'main', url: 'https://github.com/viksgeorgiev/Selenium-IDE-Jenkins.git'
            }
        }
            
       stage("Build"){
            steps{
                bat 'dotnet build SeleniumIde.sln --configuration Release'
            }
        }
        stage("Run Tests"){
            steps{
                bat 'dotnet test SeleniumIde.sln --logger "trx;LogFileName=TestResults.trx"'
            }
        }
    }
}