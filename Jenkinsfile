pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' // testando 
            }
        }
        stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' // testando 
            }
        }
      stage('Teste Kubectl') {
            steps {
              withKubeConfig([credentialsId: 'kubeconfig', serverUrl: '']) {
              sh 'kubectl get nodes'
            }
        }   
      }
    } 
} 