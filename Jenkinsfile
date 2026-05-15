pipeline {
    agent any

    stages {
        stage('Check Newman') {
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'newman -v'
            }
        }

        stage('Run Postman Collection') {
            steps {
                sh '''
                mkdir -p reports

                newman run postman/DEMO-API.postman_collection.json \
                -e postman/SIT.postman_environment.json \
                -r cli,html \
                --reporter-html-export reports/newman-report.html
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/newman-report.html', fingerprint: true
        }
    }
}