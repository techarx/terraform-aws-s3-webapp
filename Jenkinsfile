#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    publishModule()
    publishVersion()
}

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
        tar file: 's3-webapp.tar.gz', compress: true, dir:'/vnet'
        
    }
}




