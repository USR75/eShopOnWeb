pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
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

        stage('functional') {
          steps {
            sh '''dotnet test tests/FunctionalTests














'''
          }
        }

      }
    }

    stage('Deployement') {
      steps {
        sh 'dotnet publish eShopOnweb.sln -o /var/aspnet'
      }
    }

  }
}