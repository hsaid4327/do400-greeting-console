pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }
        stage("Test2"){
            steps{
                echo "Test2"
            }
        }

        // Add the Release stage here
        stage('Release') {
            steps {
                sh '''
                    oc project hsaid-greetings
                    oc start-build greeting-console  --follow --wait
                '''
            }
        }
    }
}
