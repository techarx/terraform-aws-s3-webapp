#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    postModule()
}

def filePath = "workspace/publish-module"
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
            curl -X PUT file=@webapp.tar.gz  https://archivist.terraform.io/v1/object/dmF1bHQ6djI6WWUxZkUvMkdWM3A5cjQwSzlXTEhWTFJiQjRINFI4Q0FEbU9OQnRqVS8xM3U2WjNXYmhaVlJZWmMrRFlvQ0U2Ri9tamRRWDc2ajdMVEFjSllxUzRCVGVRQkpjRmYxeGxUZ1hKcTZIY0FJem5rZlJkOUUwc3Q2MG1ncndJWkxwSlVueXN6cWtKSFVVOTJYbjRLdnBLSm02ZklJUm9WdGhkOHg4Lys5d1ZGMWJ2SlNzVGZ5TzQvV2dET01MR29tN3V3Tklsb0xrcGE4ck5KSDlMZ0lwajZwK01NYTNUNW13Z3V0MnBTeWdxbCtWZ2QzUUVyd3ZueG15VU9GVjNDTVNSNmRyQnc4ZWZsdVY5MS9HUVpnRkJTSGpTZDVObzJoKzFlUUxjU0Z1SWVJNjdrKzUrNE5qMUJPWlA1MmRLcnJreFd1N2ozSC9xQ2tvcVduODYrVzlBa2w0NmY2UE09/upload
         '''
    }
}





