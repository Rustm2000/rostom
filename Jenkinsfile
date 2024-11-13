pipeline {
    agent { label 'Jenkins-Agent' }  // Fixed agent label
    tools { 
        jdk '/usr/lib/jvm/java-11-openjdk-amd64'
        maven '/opt/apache-maven-3.6.3'
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
    }
}
