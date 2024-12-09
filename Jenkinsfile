pipeline {
    agent any
    
    environment {
    	SONAR_SCANNER_HOME = tool 'sonarqube-scanner-621';
	}
    stages {
        stage('checkout code') {
            steps {
                git branch: 'dev', credentialsId: '28e7f08d-193c-45d2-817c-632398395b21', url: 'https://github.com/daudsemab/calculator-api'
            }
        }
        stage('sonarqube analysis') {
            steps {
                sh '''
                $SONAR_SCANNER_HOME/bin/sonar-scanner \
                  -Dsonar.projectKey=CalculatorAPI \
                  -Dsonar.sources=calculator.py \
                  -Dsonar.host.url=http://sonarqube:9000 \
                  -Dsonar.token=sqp_98d81e013d60d5565a97546b86c0546be65c77d0
                  '''
            }
        }
        stage('build docker image') {
            steps {
                sh '''
                docker --version \
                echo "building docker image" \
                docker build . \
                echo "Successfully Build Docker Image"
                '''
            }
        }
    }
}

