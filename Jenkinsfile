#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
   postModule()
   
}

def filePath = "/var/lib/jenkins/workspace/publish-module"
def fileExt = '.tar.gz'
def filename = 'webapp'
def file = filename + fileExt

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
        
        
    }
}

def postModule() {
    stage('Posting') {
         sh'''#!/bin/bash -xe
         curl -v -T "file=@/var/lib/jenkins/workspace/publish-module/webapp.tar.gz" https://archivist.terraform.io/v1/object/dmF1bHQ6djI6R3NHNk1iTWRTd1JraTVFMnJoVzNDVXkxcmJKdjBUcjR2SDk2N01zbUQ1SWpNRWMrMG85bTgyU1J3enF6bTN4UUtzcVY4UjA0VWpMbVZzakZTZzlva2RqZnRtZHFnSGVtTENpWFVMLzFaZ1VsYlpIVWREZHFqUWcyRTM0Z090OE1BdDNKSUNXcEl2d3AwMUowRDI4N3gxUFQwMlRad05WZURsUjBOMGh6b2ZjMXJISnZQRDRRMVBMdWRnSDJYSFNNSmhGN1dwRG1FcDRnckZuNGplbHZ6Umx2amZMV05QOEpaMnJjdlpScGdPMmJzL3F6aHF2YTVyZFlqVzRUVDBobU9TMTFmdS9qSE5kT1BNOWRTUmV1bTllQXVMbEU2SWk2TVRna0pjaHNsdkxHd1k5a0pYcnFkYkd4NmZZRWQvR3VRdUhWNEdhRGk4akk0YmVSNC8zVGVUVVRBQkU9
            
           '''
    } 
}





