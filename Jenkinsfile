#!groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

node {
    checkout()
    publishModule()
}

def checkout() {
    stage('Clone') {
        git branch: 'master', url: 'https://github.com/techarx/terraform-aws-s3-webapp.git'
    }
}

def modulePayload() {
    def payload = """
{
  "data": {
    "attributes": {
      "vcs-repo": {
        "identifier":"techarx/terraform-aws-s3-webapp",
        "oauth-token-id":"ot-miPwwcgkGQhbrKmr",
        "display_identifier":"techarx/terraform-aws-s3-webapp"
      }
    },
    "type":"registry-modules"
  }
}
    """
    return payload
}

def publishModule() {
    def payload = modulePayload()
    def response = httpRequest(
        customHeaders: [
            [ name: "Authorization", value: "Bearer" + HGweVlbMfDzUHQ.atlasv1.fnflQ9xMWRVL74iwDvqCgizBnMyF0UjgiPC9QkS7u3NhMZkRkqfam6lDcEXZbUqcZZg ],
            [ name: "Content-Type", value: "application/vnd.api+json" ]
        ],
        httpMode: 'POST',
        requestBody: "${payload}",
        url: "https://app.terraform.io/api/v2/organizations/TFEPOC/registry-modules/vcs"
    )
}