pipeline {
  agent { docker { image 'ruby:3.2.2' } }
  
  stages {
    stage('Checkout') {
        steps {
           git branch: 'master', url: 'https://github.com/pvlamkhtn/jenkins_demo.git'
        }
    }
    
    stage('bundle install') {
    	steps{
	      withEnv(["PATH=$HOME/.rbenv/shims/bundle", "RBENV_SHELL=sh"]){
		      //sh 'gem install bundler'
		      sh 'bundle install --jobs 4'
		    }
    	}
    }
    
    // stage('Test') {
    //     steps {
    //        sh 'bundle exec rspec'
    //     }
    // }
    
    // stage('Build') {
    //     steps {
    //       sh 'bundle exec rails assets:precompile'
    //       // Additional build steps here
    //   }
    // }
    
    // Deployment stage (optional, if deploying locally)
    // stage('Deploy') {
    //     steps {
    //       // Add deployment steps here if deploying locally
    //     }
    // }
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
