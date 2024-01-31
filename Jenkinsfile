pipeline {
  agent any
  
  stages {
    stage('Checkout') {
        steps {
           git branch: 'master', url: 'ssh://git@github.com:pvlamkhtn/jenkins_demo.git/'
        }
    }
    
    stage('Install Dependencies') {
        steps {
           sh 'bundle install'
        }
    }
    
    stage('Test') {
        steps {
           sh 'bundle exec rspec'
        }
    }
    
    stage('Build') {
        steps {
          sh 'bundle exec rails assets:precompile'
          // Additional build steps here
      }
    }
    
    // Deployment stage (optional, if deploying locally)
    stage('Deploy') {
        steps {
          // Add deployment steps here if deploying locally
        }
    }
  }

  post {
    success {
        echo 'Build succeeded! Sending notifications...'
        // Add notification steps here
    }
    failure {
        echo 'Build failed! Sending notifications...'
        // Add notification steps here
    }
    always {
        echo 'Archiving artifacts...'
        archiveArtifacts artifacts: 'path/to/artifacts/**/*', allowEmptyArchive: true
    }
  }
}
