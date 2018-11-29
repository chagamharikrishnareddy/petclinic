pipeline {
    agent any 
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/chagamharikrishnareddy/petclinic.git'

            }
        }
        stage('Build') { 
            steps {
                withSonarQubeEnv('SonarQube') {
                 sh 'mvn clean package sonar:sonar'
            }
        }
        }
        stage ('Junit') {
            steps {
                 junit 'target/surefire-reports/*.xml'
            }
        }

      stage ('s3 deploy')  {
      
             steps {
                 s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'krishbucket12', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-2', showDirectlyInBrowser: false, sourceFile: '**/', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 'krishbucket', userMetadata: []

                 
             }
            }
            
        }
}
    

      

