pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean install -B'
            }
        }
        stage('Sonar') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw -B clean verify sonar:sonar -Dsonar.projectKey=spring-petclinic-angular -Dsonar.host.url=http://10.68.32.75:9000 -Dsonar.login=a3cf37e24ddf4a766359453935ece221232b0333'
            }
        }        
    }
}
