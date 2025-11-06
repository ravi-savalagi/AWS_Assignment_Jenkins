pipeline {
    agent any

    environment {
        ENDPOINT = 'https://qquae6prhk.execute-api.us-east-1.amazonaws.com'
        MY_IP = '167.103.6.167/32'
        ACTION = "${params.ACTION}"
        INSTANCE_ID = "${params.INSTANCE_ID}"
    }

    parameters {
        string(name: 'ACTION', defaultValue: 'create', description: 'EC2 action: create, start, stop, terminate')
        string(name: 'INSTANCE_ID', defaultValue: '', description: 'EC2 instance ID (if needed)')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Lambda API Trigger') {
            steps {
                bat 'python lambda_api_runner.py'
            }
        }
    }
}