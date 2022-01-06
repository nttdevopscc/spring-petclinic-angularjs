pipeline {
    agent any
    tools {
        maven 'Maven 3.3.3'
    }
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
                // sh './mvnw -B clean verify sonar:sonar -Dsonar.projectKey=spring-petclinic-angular -Dsonar.host.url=http://10.0.2.38:9000/sonarqube -Dsonar.login='
            }
        }
        stage('Docker') {
            steps {
                echo 'Build docker image'
                 sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
                sh './mvnw clean install'
                sh 'cd spring-petclinic-server'
                sh 'mvn -B clean package docker:build -e'
            }
        }        
    }
}
