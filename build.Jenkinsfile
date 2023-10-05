pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')
                ]) {
                    sh '''
                    docker login --username $USERNAME --password $PASSWORD
                    docker build -t roberta:latest .
                    docker tag roberta:latest gaurav1954/roberta:latest
                    docker push gaurav1954/roberta:latest
                    '''
                }
            }
            post{
                success{
                   sh 'docker images prune -a -f --filter until=24h'

                }
            }
        }
        //wait false means dont wait to deploy pipeline to finish just trigger it and forget
        stage('Trigger Deploy'){
            steps{
                build job:'RobertaDeploy', wait:false, parameters:[
                    string(name:'Roberta_image_url',value:'gaurav1954/roberta:latest')
                ]
            }          
        }
    }
}