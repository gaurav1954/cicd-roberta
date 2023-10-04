pipeline{
    agent any
    parameters{ string(name:'Roberta_image_url', defaultValue:'',description:'')}
    stages{
        stage('Deploy'){
            steps{
                sh 'echo $Roberta_image_url'
                sh 'echo "deploying"'
            }
        }
    }



}