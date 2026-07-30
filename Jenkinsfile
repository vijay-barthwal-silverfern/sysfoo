pipeline {
    agent any

    tools {
        maven 'Maven 3.9.16'
    }

    stages {

        stage('Build') {
            steps {
                echo "Compiling the mamaven job"
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                 echo "testing the mamaven test"
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                 echo "Package the mamaven job"
                sh 'mvn package -DskipTests'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar, target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }

        always {
            cleanWs()
        }
    }
}
