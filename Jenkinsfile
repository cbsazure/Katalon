pipeline {
    agent {
        docker {
            // Specify the Katalon Docker image
            image 'katalonstudio/katalon'
            args '-v /Users/Akhil/home/Katalon:/tmp/project'
            // Mount the Katalon directory from the host to /tmp/project in the container
        }
    }
    stages {
        stage('Run Katalon Tests') {
            steps {
                script {
                    // Run Katalon commands inside the Docker container
                    sh '''
                        cd /tmp/project/KatalonTesting
                        katalonc.sh -projectPath="/tmp/project/KatalonTesting" -retry=0 -testSuitePath="Test Suites/Suite1" -browserType="Chrome" -executionProfile="default" -apiKey="YOUR_API_KEY"
                    '''
                    // Adjust the command with your specific test suite path and API key
                }
            }
        }
    }
}

