pipeline {
    agent {
        docker {
            // Use an image that includes Docker CLI (e.g., 'docker' or 'docker:20.10')
            image 'docker'
            args '-v /Users/Akhil/home/Katalon:/tmp/project'
            // Mount the Katalon directory from the host to /tmp/project in the container
        }
    }
    stages {
        stage('Test Docker Connectivity') {
            steps {
                script {
                    // Test Docker connectivity by listing containers
                    sh 'docker ps'
                }
            }
        }
        
        stage('Run Katalon Tests') {
            steps {
                script {
                    // Run Katalon commands inside the Docker container
                    sh '''
                        cd /tmp/project/KatalonTesting
                        katalonc.sh -projectPath="/tmp/project/KatalonTesting" -retry=0 -testSuitePath="Test Suites/Suite1" -browserType="Chrome" -executionProfile="default" -apiKey="6052bbfe-f4fc-4553-b334-6769d9eff78b"
                    '''
                    // Adjust the command with your specific test suite path and API key
                }
            }
        }
    }
}
