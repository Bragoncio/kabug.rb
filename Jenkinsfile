pipeline{
    agent {
        docker{
            image "qaninja/rubywd"
        }
    }
    stages {
        stage('Build'){
            steps {
                echo 'Building or Resolve Dependencies'
                sh 'rm -f Gemfile.lock'
                sh 'bundler install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                sh 'bundle exec cucumber -p ci '
            }
        }
        stage('UAT'){
            steps{
                echo 'Wait for User Acceptance'
                input(message: 'Go to production ?', ok:'yes')
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp is Ready :)'
            }
        }
    }
    
    
}