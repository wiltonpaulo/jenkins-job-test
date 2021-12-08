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
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Demo') {
            steps {
                sayHello 'Wilton'
            }
        }
        stage("Dashboard settings") {
            steps {
                script {
                    def lastSuccessfulBuildID = 0
                    def lastSuccessfulBuildstartTimeInMillis = ""
                    def lastSuccessfulBuildDate
                    def build = currentBuild.previousBuild
                    while (build != null) {
                        if (build.result == "SUCCESS")
                        {
                            lastSuccessfulBuildID = build.id as Integer
                            lastSuccessfulBuildResult = build.result
                            lastSuccessfulBuildstartTimeInMillis = build.startTimeInMillis
                            lastSuccessfulBuildDate = sh(script: 'echo $lastSuccessfulBuildstartTimeInMillis | date -u', returnStdout: true)                            
                            break
                        }
                        build = build.previousBuild
                    }
                    def ResultMessage = sh(script: 'uname -s', returnStdout: true)
                    
                    println ResultMessage
                    jobDuration = (System.currentTimeMillis() - currentBuild.startTimeInMillis)/1000;
                    currentBuild.description = "Result build: " + ResultMessage \
                                            + "<br> Duration: " + jobDuration + " sec" \
                                            + "<br>Last successful build: " + "<a href=" + JENKINS_URL + "job/" + JOB_NAME + "/" + lastSuccessfulBuildID + ">" + lastSuccessfulBuildID + "</a>" \
                                            + "<br>Last build date: " + lastSuccessfulBuildDate
                }
            }
        }
    }
}
