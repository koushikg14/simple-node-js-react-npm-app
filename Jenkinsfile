pipeline {
    agent {
        docker {
            image 'node:lts-bullseye-slim'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }

        stage("npm release") {
      steps {
        script {
          // bump versions only for main or release branch builds
          if (true) {
            sh ("npx semantic-release --debug")
          } else {
            echo "This is not a candidate branch for version bump.  Skipping ..."
          }
          // TODO - stop build if there is nothing to release
        }
      }
    }
    }
}