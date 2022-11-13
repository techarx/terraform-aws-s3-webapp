#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    postModule()
}

def filePath = "workspace/publish-module/"
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
            curl --upload-file webapp.tar.gz  https://archivist.terraform.io/v1/object/dmF1bHQ6djI6eUtDbElvbnQ4cjlRalpYSTkyY3dYYTBxZnhoK0w4V1ljV2I5bWJYb2p2QUFjMVAwT2F1WUxHZTZEOEQ2TkRwc1BmZnMxb0dQMmhMODRlTld3bjYyTTdHR0F0REpINW45KzdNZkMxc0JYTjdYRlBTMmdVN0prVEVYOXo5YWV5enhuTUhvRHE1d2J4eUFMeE9hVzhMbkRqcEdwQWwzQ05WOTNCalpDa2pJaTloNGUvbjFwdDVsVjkwYjZzQ3M5WmdrZjBja1lmcVVnc1Q0QnZuNUZKR3JENzdxWWs4ZkJELzQ2NWluckhENDhxNStHd3pKenFhM2MrM3ZSaktDWmVkYWl3UlJDOGFDT1lCYVZRdU1pd0kvdUFvZnJOVmZkNUJFTnc0QVpSVlEwQlpybVRIVm9HZjYrcERDMVB2N29pY1JtV2dQL2RoMDd1YXFZSk0yc0JJK1RZYytMeUE9
         '''
    }
}





