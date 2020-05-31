pipeline {
    agent any
    stages {
        stage('Upload') {
            dir('https://github.com/gobrando/static') {
                pwd()
                withAWS(region:'us-east-2', credentials:'aws-static') {
                    def identity=awsIdentity()
                    s3Upload(pathStyleAccessEnabled: true, 
                        payloadSigningEnabled: true, 
                        file: "index.html", 
                        bucket:"jenkins-pipeline-uda")
                }
            }
        }
    }
}