#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
   checkout()
   publishModule()
   postModule()
   
}


//def filePath = "/var/lib/jenkins/workspace/publish-module"
//def fileExt = '.tar.gz'
//def filename = 'webapp'
//def carry = readFile "${env.WORKSPACE}/webapp.tar.gz"

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
        tar file: 'webappss.tar.gz', compress: true, dir:'./vnet'
        
        
    }
}



def modulePayload() {
    def payload = """
{
  "data": {
    "type": "registry-modules",
    "attributes": {
      "name": "s3-module",
      "provider": "aws",
      "registry-name": "private"
    }
  }
}

    """
    return payload
}

def publishModule() {
    def payload = modulePayload()
    def response = httpRequest(
        customHeaders: [
            [ name: "Authorization", value: "Bearer " + env.BEARER_TOKEN ],
            [ name: "Content-Type", value: "application/vnd.api+json" ]
        ],
        httpMode: 'POST',
        requestBody: "${payload}",
        url: "https://app.terraform.io/api/v2/organizations/TFEPOC/registry-modules"
    )
}

def versionPayload() {
    def Payload = """
{
  "data": {
    "type": "registry-module-versions",
    "attributes": {
      "version": "1.2.3"
    }
  }
}


    """
    return Payload

}



def publishVersion() {
    def Payload = versionPayload()
    def response = httpRequest(
        customHeaders: [
            [ name: "Authorization", value: "Bearer " + env.BEARER_TOKEN ],
            [ name: "Content-Type", value: "application/vnd.api+json" ]
        ],
        httpMode: 'POST',
        requestBody: "${Payload}",
        url: "https://app.terraform.io/api/v2/organizations/TFEPOC/registry-modules/private/TFEPOC/s3-module/aws/versions"
    )
    def data = new JsonSlurper().parseText(response.content)
    println ("link: " + data.data.links.upload)
    return data.data.links.upload
}


def postModule() {
    def URL = publishVersion()
    def carry = load "${env.WORKSPACE}/webappss.tar.gz"
    def response = httpRequest(
        customHeaders: [[ name: "Content-Type: application/octet-stream" ]],
        httpMode: 'PUT',
        requestBody: "${carry}",
        url: "${URL}"
    )
}




