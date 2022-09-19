pipeline {
    agent any

    environment {
        PATH = "${PATH}:${getTerraformPath()}"
    }

    stages{

        stage('Dev - init'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'
                sh "terraform init"
            }
        }

        stage('Dev - apply'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'
                sh "terraform apply -auto-approve -var-file=dev.tfvars"
            }
        }

        stage('Dev - destroy'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'
                sh "terraform destroy -auto-approve"
            }
        }

        stage('Prod - init'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new prod'
                sh "terraform init"
            }
        }

        stage('Prod - apply'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new prod'
                sh "terraform apply -auto-approve -var-file=prod.tfvars"
            }
        }

        stage('Prod - destroy'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new prod'
                sh "terraform destroy -auto-approve"
            }
        }


    }
}


def getTerraformPath(){
    def tfHome = tool name: 'terraform1.2', type: 'terraform'
    return tfHome
}