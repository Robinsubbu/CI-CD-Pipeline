pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'   // Make sure Maven is configured in Jenkins (Manage Jenkins → Tools)
        jdk 'JAVA_HOME'       // Optional: If you’ve configured a specific JDK
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/Robinsubbu/CI-CD-Pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project using Maven...'
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving JAR files...'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Post Build Notification') {
            steps {
                echo 'Build completed successfully!'
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded!!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
