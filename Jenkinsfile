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

        // Add the "Deploy" stage here
        stage('Deploy') {
            steps {
		sh '''
                    oc login -u eddvqe -p bbb6323c10d94050ba80 https://api.na46a.prod.ole.redhat.com:6443
		    oc project eddvqe-greetings
                    oc start-build greeting-service --follow --wait
                '''
            }
       }
    }
}
