pipeline {
    agent any

    environment {
        PATH = "${PATH}:${getTerraformPath()}"
    }

    stages{

        stage('Dev - init and apply'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'
                sh "terraform init"
                sh "terraform apply -auto-approve -var-file=dev.tfvars"
            }
        }

        stage('Dev - destroy'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new dev'
                sh "terraform destroy -auto-approve"
            }
        }

        stage('Prod - init and apply'){
            steps{
                sh returnStatus: true, script: 'terraform workspace new prod'
                sh "terraform init"
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