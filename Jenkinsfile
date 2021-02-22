pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage("Guild Docker Image') {
              when {
                  branch 'master'
              }
              steps{
                  app = docker.build("abhiv22/train-schedule)
                  app.inside {
                      sh 'echo $(curl localhost:8080)'
                  }
               }
           }
        }
    }
}
