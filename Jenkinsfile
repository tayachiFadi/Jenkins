pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShop.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}