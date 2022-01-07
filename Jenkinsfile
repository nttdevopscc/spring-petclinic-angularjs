pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean install'
            }
            post {
              always {
                // One or more steps need to be included within each condition's block.
                junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'spring-petclinic-server/target/*.jar', followSymlinks: false
              }
            }
        }
    }
}
