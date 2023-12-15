pipeline {
    agent any
    
    stages {
        stage('Test Docker Connectivity') {
            steps {
                script {
                    // Set the Docker socket path
                    env.DOCKER_HOST = 'unix:///Users/Akhil/.docker/run/docker.sock'
                    // Run a Docker command to test connectivity (e.g., list Docker containers)
                    sh 'docker ps'
                }
            }
        }
        
        stage('Run Katalon Tests') {
            agent {
                docker {
                    // Specify the Katalon Docker image
                    image 'katalonstudio/katalon'
                    args '-v /Users/Akhil/home/Katalon:/tmp/project'
                    // Mount the Katalon directory from the host to /tmp/project in the container
                }
            }
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
