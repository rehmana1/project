pipeline {

  environment {

    registry = "rehmana1/project"

    registryCredential = 'Aziz.261290'

    dockerImage = ''

  }

  agent any

  tools {nodejs "AzR_NodeJS" }

  stages {

    stage('Cloning Git') {

      steps {

        git 'https://github.com/SimplilearnDevOpsOfficial/DockerizeJenkins.git'

      }

    }

    stage('Build') {

       steps {

         sh 'npm install'

         sh 'npm run bowerInstall'

       }

    }

    stage('Test') {

      steps {

        sh 'npm test'

      }

    }

    stage('Building image') {

      steps{

        script {

          dockerImage = docker.build registry + ":$BUILD_NUMBER"

        }

      }

    }

    stage('Deploy Image') {

      steps{

         script {

            docker.withRegistry( '', registryCredential ) {

            dockerImage.push()

          }

        }

      }

    }

  }

}
