pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hi, this is Zulaikha from edureka'
                 }
                 }

    stage('SonarQube analysis') {
      steps {
        script {
          // requires SonarQube Scanner 2.8+
          scannerHome = tool 'sonarQ'
        }
        withSonarQubeEnv('sonarQ') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  
               
           
                
                 stage('SonarQube Quality Gate') {
            steps {
                script {
                    timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
                        def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        } else {
                                 mail bcc: '', body: 'this bulid', cc: '', from: '', replyTo: '', subject: 'test email', to: 'akhil.h@bridge-global.com'
                           echo 'Quality is Ok :)'
                        }
                    }
                }
            }
        
                 }
             
              }
}
