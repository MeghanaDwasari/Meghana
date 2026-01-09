@'
pipeline {
    agent any

    tools {
        jdk "jdk11"   // Configure this JDK in Jenkins Global Tool Configuration
    }

    stages {
        stage("Checkout") {
            steps {
                git branch: "main",
                    url: "file:///C:/PATH/TO/pipeline-git-repo"
                echo "Repository cloned successfully"
            }
        }

        stage("Build") {
            steps {
                echo "Building application..."
                bat "build.bat"
            }
        }

        stage("Test") {
            steps {
                echo "Running tests..."
                bat "java -cp src\\main\\java;src\\test\\java com.example.HelloDevOpsTest"
            }
        }

        stage("Archive") {
            steps {
                echo "Archiving artifacts..."
                archiveArtifacts artifacts: "app.jar", fingerprint: true
                archiveArtifacts artifacts: "build.bat", fingerprint: true
            }
        }
    }

    post {
        always {
            echo "Pipeline completed"
            cleanWs()
        }
    }
}
'@ | Out-File Jenkinsfile -Encoding utf8
