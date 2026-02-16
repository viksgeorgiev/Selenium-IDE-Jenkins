pipeline{
    agent any
    stages{
        stage("Checkout code"){
            steps{
                git branch: 'main', url: 'https://github.com/viksgeorgiev/Selenium-IDE-Jenkins.git'
            }
        }
          stage("Set up .NET Core"){
            steps{
                bat '''
                echo Installing .NET SDK 6.0
                choco install dotnet-sdk --version=6.0.100 -y
                '''
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