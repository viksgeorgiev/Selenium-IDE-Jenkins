pipeline{
    agent any
    stages{
        stage("Checkout code"){
            steps{
                git branch 'main', url: 'https://github.com/viksgeorgiev/Selenium-IDE-Jenkins.git'
            }
        }
          stage("Set up .NET Core"){
            steps{
                bat '''
                echo Installing .NET SDK 6.0
                choco install dontet-sdk -y --version=6.0.100
                '''
            }
        }
        stage("Uninstall current chrome"){
            steps{
                bat '''
                echo Uninstalling current Google Chrome
                choco install googlechrome -y
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
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}