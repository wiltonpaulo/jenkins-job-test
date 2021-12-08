// Load previous configured library by jenkins ui
// @Library('monitor-view-library') _

// Configure and load library
library identifier: 'monitor-view-library@main',
    retriever: modernSCM([
      $class: 'GitSCMSource',
      remote: 'https://github.com/wiltonpaulo/monitor-view-library.git'
])

pipeline {
    agent any

    stages {   
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                exit 1
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            buildDashboardView()
        }
    }    
}
