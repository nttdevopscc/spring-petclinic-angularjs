pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'ls -lrt'
                sh 'chmod +x mvnw'
                sh './mvnw clean package -B'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
        stage('Scan') {
            steps {
                sh 'chmod +x mvnw'
                // sh './mvnw -B clean verify sonar:sonar -Dsonar.projectKey=spring-petclinic-angular -Dsonar.host.url=http://10.68.32.75:9000 -Dsonar.login=a3cf37e24ddf4a766359453935ece221232b0333'
            }
        }
        stage('Docker') {
            steps {
                echo 'Build docker image'
                sh './mvnw clean install'
                sh 'cd spring-petclinic-server'
                sh 'mvn clean package docker:build'
            }
        }        
    }
}
