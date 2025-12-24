pipeline {
    agent any
    
    tools {
        jdk 'JDK21'  // Must match the name from Task 3
    }
    
    stages {
        stage('Hello') {
            steps {
                echo 'Pipeline started!'
                echo "Building on: ${env.NODE_NAME}"
            }
        }
        
        stage('Checkout') {
            steps {
                // The checkout happens automatically when using 
                // "Pipeline script from SCM", so no need to add an echo
            }
        }
        
        stage('Build') {
            steps {
                sh 'chmod +x mvnw' 
                sh './mvnw clean compile'  
            }
        }
        
        stage('Test') {
            steps {
                sh './mvnw test'  
            }
        }
        
        stage('Package') {
            steps {
                sh './mvnw package -DskipTests' 
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}