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
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage("Dashboard settings") {
            steps {
                script {
                    def lastSuccessfulBuildID = 0
                    def build = currentBuild.previousBuild
                    while (build != null) {
                        if (build.result == "SUCCESS")
                        {
                            lastSuccessfulBuildID = build.id as Integer
                            break
                        }
                        build = build.previousBuild
                    }
                    def Result = sh(script: 'date', returnStdout: true) 
                    println Result
                    currentBuild.description = "Result build:" + Result + "<br>Last successfull build:" + lastSuccessfulBuildID
                }
            }
        }
    }
}
