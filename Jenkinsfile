pipeline {
  agent any

  stages {
      stage('Build Artifact - Maven') {
      steps {
        sh "mvn clean package -DskipTests=true"
        archive 'target/*.jar'
      }
    }
      stage('Unit Tests - JUnit and JaCoCo') {
      steps {
        sh "mvn test"
      }
    }
      stage('Mutation Tests - PIT') {
      steps {
        sh "mvn org.pitest:pitest-maven:mutationCoverage"
      }
    }
      }
    }
      stage('Vulnerability Scan - Docker') {
        steps {
        	  "Dependency Scan": {
        		  sh "mvn dependency-check:check"
          }
      }
    }
 
      