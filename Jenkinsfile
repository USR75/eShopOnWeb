pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'donet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'donet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test/IntegrationTests'
          }
        }

        stage('functional') {
          steps {
            sh 'dotnet test tests/FonctionalTests'
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