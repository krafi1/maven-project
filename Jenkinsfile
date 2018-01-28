pipeline {
  agent any
  stages {
    stage('Init'){
      steps {
        echo "Testing..."
      }
    }
    
    stage('Build'){
      steps {
        echo 'Building...'
        bat 'mvn clean package'
      }
      post {
        success {
          echo 'Now archiving...'
          archiveArtifacts artifacts: '**/*.war'
        }
      }
    }
    
    stage('Deploy to staging'){
      steps {
        build job: 'deploy-to-staging'
        echo 'Code deployed.'
      }
    }
  }
}
