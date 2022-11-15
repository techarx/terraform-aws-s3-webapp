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
          curl --help
            
           '''
    } 
}





