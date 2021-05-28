pipeline {
  
  // Ahora el agent se pondra para los nodos
  agent {
    node {
      label 'principal'
    }
  }
  
  options {
    // Para ficheros de log
    buildDiscarder logRotator(
      daysToKeepStr: '15',
      numToKeepStr: '10'
    )
  }
  
  stages {
    
    stage('Cleanup Workspace') {
      steps {
        cleanWs()
        echo "Eliminado Workspace para Proyecto"
      }
    }
    
     stage('Code Checkout') {
      steps {
        checkout(
          $class: 'GitSCM',
          branches: [[name: '*/main']],
          userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git' ]]
        )
      }
    }
    
    stage('Unit Testing') {
      steps {
        echo "Running Unit Tests"
      }
    }
    
    stage('Code Analytics') {
      steps {
        echo "Running Code Analytics"
      }
    }
    
     stage('Build Deploy Code') {
       
       when {
        branch 'development'
       }
       
      steps {
        echo "Building Artifact"
        echo "Deploying Code"
      }
    }
    
    
  }
}
