// Example of Jenkins pipeline script

pipeline {
  stages {
    stage("Build") {
       steps {
          // Executes the Apache Maven commands, clean then package. This requires Apache Maven configuration from Jenkins
          mvn clean verify
          // List the files in current directory path by executing a default shell command
          sh "ls -ltr"
       }
   }
   // And next stages if you want to define further...
 } // End of stages
} // End of pipeline