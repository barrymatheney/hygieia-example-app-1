pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
                hygieiaDeployPublishStep applicationName: 'App name', artifactDirectory: 'app/target', artifactGroup: 'com.yourcompany.product1', artifactName: '*.jar', artifactVersion: '0.0.1', buildStatus: 'Success', environmentName: 'DEV'
            }
        }
        stage('SonarQube') {
            steps {
//                sh './gradlew -Dsonar.host.url=http://sonarqube:9000 jacocoTestReport sonarqube'
                sh './gradlew sonarqube   -Dsonar.projectKey=hygieia-example-app_master   -Dsonar.host.url=http://sonarqube:9000   -Dsonar.login=e3a7cb07763b4292be043b0c2eeae66e8b5a5661'
                hygieiaDeployPublishStep applicationName: 'App name', artifactDirectory: 'app/target', artifactGroup: 'com.yourcompany.product1', artifactName: '*.jar', artifactVersion: '0.0.1', buildStatus: 'Success', environmentName: 'DEV'
            }
        }
    }
}
