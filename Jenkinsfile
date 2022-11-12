#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    publishModule()
    publishVersion()
    
    
}

def file = "$workspace/webapp.tar.gz"

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
        
        
    }
}

def modulePayload() {
    def payload = """
{
  "data": {
    "type": "registry-modules",
    "attributes": {
      "name": "s3-webapp",
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
        url: "https://app.terraform.io/api/v2/organizations/TFEPOC/registry-modules/private/TFEPOC/s3-webapp/aws/versions"
    )
    def data = new JsonSlurper().parseText(response.content)
    def cmd = ""
        ["curl", "-T", "${file}", "${data.data.links.upload}"]
    
    
}





