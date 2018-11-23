pipeline {
    agent any 
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/chagamharikrishnareddy/petapp.git' 
            }
        }
        stage('Build') { 
            steps {
                sh 'mvn clean package'
            }
        }
        
                stage ('Junit') {
            steps {
                 junit 'target/surefire-reports/*.xml'

            }
        }

        stage('Deploy') { 
            steps {
                s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'krishbucket12', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-2', showDirectlyInBrowser: false, sourceFile: '**/*.jar', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 'aws', userMetadata: []

            }
        }
    }
}
