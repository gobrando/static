pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload') {
            steps {
                withAWS(region:'us-east-2', credentials:'aws-static') {
                    s3Upload(pathStyleAccessEnabled: true, 
                        payloadSigningEnabled: true,  
                        bucket:"jenkins-pipeline-uda", 
                        includePathPattern:'**/*',
                        path: 'index.html')
                }
            }
        }
    }
}