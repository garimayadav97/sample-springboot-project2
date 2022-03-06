// Example of Jenkins pipeline script

node {
        stage('Initialize')
        {
            def dockerHome = tool 'dockerTool'
            //env.PATH = env.PATH + ":${dockerHome}"
        }

        try {
                stage("Checkout") {
                      git branch: 'master',
                        url: 'https://github.com/garimayadav97/sample-springboot-project.git'
           
                }
                stage("Maven Build") {
                      bat "mvn clean install"
                }
                stage("Unit Tests") {
                      //bat "mvn verify"
                }
                stage("Docker Build and Tag") {
                      app = docker.build("lucas/sample-app")
                }
                stage("Docker Push") {
                      //bat "docker build -t springio/gs-spring-boot-docker ."
                }
        }
        catch (Exception e) {
          currentBuild.currentResult : 'FAILURE'
          echo 'Exception occurred: ' + e.toString()
          emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}, build ${env.BUILD_NUMBER} failed\nMore info at: ${env.BUILD_URL}",
                    recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                    subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
    }

} // End of pipeline