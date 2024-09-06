pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This is where we fetch the code from the repository
                git branch: 'main', url: 'https://github.com/GANWEIJIA/Java_Gradle_Responsive_Website'
                echo 'Checkout successful!'
            }
        }
        stage('Build') {
            steps {
                // Build the project using Gradle wrapper
                script {
                    try {
                        powershell './gradlew.bat clean build'  // Adjust this if you're using Windows
                        echo 'Congratulation, build successful!!'
                    } catch (Exception e) {
                        echo 'Build failed!'
                        throw e  // Re-throw the exception to mark the build as failed
                    }
                }
            }
        }
        stage('Test') {
            steps {
                // Run the tests
                script {
                    try {
                        powershell './gradlew.bat test'
                        echo 'Tests executed successfully!'
                    } catch (Exception e) {
                        echo 'Tests execution failed!'
                        throw e  // Re-throw the exception to mark the build as failed
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
        always {
            echo 'Cleaning up workspace'
            deleteDir()
        }
    }
}
