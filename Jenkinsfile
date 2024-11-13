pipeline {
    agent { label 'Jenkins-Agent' }  // Fixed agent label
    tools { 
        jdk 'Java11'
        maven 'Maven3'
    }
    stages {
        stage("Cleanup workspace") {
            steps {
                cleanWs()  // Cleanup workspace
            }
        }
        stage("Checkout from SCM") {
            steps {
                // Pull the latest code from the repository
                git branch: 'main', url: 'https://github.com/Rustm2000/rostom.git'
            }
        }
        stage("Build Application") {
            steps {
                sh "mvn clean package"  // Build application
            }
        }
        stage("Test Application") {
            steps {
                sh "mvn test"  // Run tests
            }
        }
        stage("SonarQube Analysis") {
            steps {
                script {
                    // Run SonarQube analysis
                    withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token') { // This is your SonarQube instance name in Jenkins
                        sh 'sonar-scanner'
                    }
                }
            }
        }
    }
}
