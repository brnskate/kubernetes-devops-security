pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' // testando 
            }
        }
        stage('Unit Tests - JUnit and JaCoCo') {
          steps {
            sh "mvn test"
            }
          post{
            always { 
              junit 'target/surefire-reports/*.xml'
              jacoco execPattern: 'target/jacoco.exec'
          }
           }
           stage('Vulnerability Scan - Docker') {
               steps {
                 sh " mvn dependency-check:check"
               }
           post{
               always {
                 dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
           }
         } 
      }    
    }
  }
}  