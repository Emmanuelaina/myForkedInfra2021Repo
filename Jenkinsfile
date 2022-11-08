pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Emmanuelaina/myForkedInfra2021Repo']]])
            }
        }
        
        stage("terraform init") {
            steps {
                sh ("terraform init -reconfigure")
            }
        }
        
        stage("plan") {
            steps {
                sh ("terraform plan")
            }
        }
        
        stage ("action") {
            steps {
                echo "Terraform action is ---> ${action}"
                sh ("terraform ${action} --auto-approve")
            }
        }
    }
}
