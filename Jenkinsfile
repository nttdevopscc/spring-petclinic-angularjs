pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw -B clean install'
            }
            post {
              always {
                junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'spring-petclinic-server/target/*.jar', followSymlinks: false
              }
            }
        }
    }
}
