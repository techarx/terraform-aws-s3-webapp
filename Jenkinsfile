#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    postModule()
}

def filePath = "publish-module/workspace"
def fileExt = '.tar.gz'
def filename = 'webapp'
def file = filePath + filename + fileExt

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
        
        
    }
}

def postModule() {
    stage('Posting') {
        sh'''#!/bin/bash -xe
            cd ${filePath}
            curl -X POST file=@{filename}.tar.gz  https://archivist.terraform.io/v1/object/dmF1bHQ6djI6NGtMMXZWV29VU053MVNRc0daWDdvY0N5YytWMFBTMkh2c2doY1ROMXVsbERmcnhrQms1T05FQi83RnpicnVIRndTUHFmNDZ5YVFrbXdHS2xjaVo0ODdNeDFKVmtYbmwwVmttbW13R05Sc0JZVkk1akRjYzZwcm9ITEd3c1VhWjBROWtLcGU2d2JvdU5CRFhxM0d1akduTk9Ed2NJaEtEZEpKcWYwdGNKOUxVdzBkeFF5Qk1CYmFVeFh6OGFzQ0M0Y3FyU080Yjlld1h4NkZZT1hvdGtHMyt3ZUVEMmFodkJBUE5iQUQ1OVdXS3V5eHBOTmVvOE9QdGVwaTFUYzFoRHN3ZmhiWEFLYVhaYkptaGxkQlQ2VnZlNVlkZ1h3UDQxSjh4T09xUWZaMUw1L0RmZ2JQTFFZNjFXOHFOdW1saW9UTnlXTFdWZExiNjRRMG8yYTA3UTdpODhzK009
         '''
    }
}





