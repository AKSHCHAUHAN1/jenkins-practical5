pipeline {
    agent any

    tools {
        maven 'Maven-Homebrew'
    }

    stages {
        stage('Checkout Verification') {
            steps {
                sh '''
                    echo "Repository checked out successfully"
                    git log -1 --oneline
                '''
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test Artifact') {
            steps {
                sh '''
                    echo "Checking generated artifact..."
                    ls -lh target/
                    test -f target/jenkins-practical5-1.0-SNAPSHOT.jar
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline from Git completed successfully!'
        }
    }
}
