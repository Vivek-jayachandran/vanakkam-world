pipeline { 
 environment{
  registry = "vivekdevopsfree/tom"
  dockerImage= ""
agent any
 tools{
    maven 'mymaven'
 }
 
     stages {
         stage ('get code') {
            steps {
                git 'https://github.com/Vivek-jayachandran/vanakkam-world'
                  }
              }
      
    stage ('maven') {
         steps {
           sh 'mvn clean package'
                }
              }
      
      stage ('Build image') {
          steps {
           dockerImage = docker.build registry + ":$BUILD_NUMBER"
          }
      }
  }
 }
}
