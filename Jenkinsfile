pipeline {
    agent any // deploy on any available agent
    stages {
        stage('Checkout') { // Stage for checking out the code from the repository
            steps {
                git branch: 'master', url: 'https://github.com/IstiqlalDunya/Hello-world-java-jenkins.git'
            }
        }
        stage('Build') {
            steps { bat 'gradlew clean build'} 
            // use {powershell 'gradle clean build'} to run local machine's Gradle version.
        }
        stage('Test') {
            steps { bat 'gradlew test'}
        }
        stage('Deploy') {
            steps { powershell 'java -jar build/libs/hello-world-java-V1.0.jar'}           
        }    
}

post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
    
}
