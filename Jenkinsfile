// Example of Jenkins pipeline script

pipeline {
    agent any
  stages {
    stage("Build") {
       steps {
          mvn clean verify
          sh "ls -ltr"
       }
   }
   // And next stages if you want to define further...
 } // End of stages
} // End of pipeline