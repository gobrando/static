pipeline {
    agent any
    stages {
        stage('Upload') {
            steps {
                dir('https://github.com/gobrando/static') {
                    pwd()
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
}