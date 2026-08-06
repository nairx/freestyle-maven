pipeline {
    agent any
    tools{
        jdk 'JDK21'
        maven 'Maven3'
    }
    stages{
        stage('Checkout'){
            steps{
                git branch:'main',url:'https://github.com/nairx/freestyle-maven.git'
            }
        }
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
        }
        stage('Deploy'){
            steps{
                bat 'copy target\\freestyle-maven-1.0-SNAPSHOT.jar D:\\freestyle-maven\\hello.jar'
            }
        }
        stage('Run Application'){
            steps{
               bat '''
                taskkill /F /IM java.exe || exit 0
                start java -jar D:\\freestyle-maven\\hello.jar
                '''
            }
        }
    }
     post {
        always {
            archiveArtifacts artifacts: 'target/*.jar'
        }
    }
}