pipeline {
    agent any

    tools {
        jdk 'jdk11'   // Must match Jenkins Global Tool Configuration
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
                bat 'build.bat'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving artifacts...'
                archiveArtifacts artifacts: 'app.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
            cleanWs()
        }
        success {
            echo 'BUILD SUCCESS'
        }
        failure {
            echo 'BUILD FAILED'
        }
    }
}
