pipeline{
    agent{label 'master'}
    tools{
        maven 'Maven'
    }
    stages{
        stage('Checkout'){
            steps{
                    git 'https://github.com/AnjuMeleth/spring-petclinic.git'
                 }
        }
        stage('Build'){
            steps{
                    bat 'mvn clean compile' 
                 }
        }  
        stage('Test'){
            steps{
                    bat 'mvn test'
                    junit '**/target/surefire-reports/TEST-*.xml'
                 }
        }
        stage('Package'){
            steps{
                    bat 'mvn package'
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                 }
        }
        stage('Reports'){
            steps{
                    bat 'mvn verify'
                    publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])     
                 }
        }   
    }
} 
