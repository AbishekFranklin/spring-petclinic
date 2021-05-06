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
    }
} 
