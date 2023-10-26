pipeline{
    agent any
    parameters{ string(name:'Roberta_image_url', defaultValue:'',description:'')}
    options{disableConcurrentBuilds()} //bugfix
    stages{
        stage('Deploy'){
            steps{
                sh 'echo $Roberta_image_url'
                sh 'echo "deploying"'
            }
        }
    }



}