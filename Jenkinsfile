pipeline{
    agent any
    stages{
     stage('CodeScan'){
        steps{
            sh 'trivy fs . -o result.hcl' 
            sh 'cat result.hcl'
            
        }
    }
    stage('dockerImageBuild'){
        steps{
            sh 'docker -v'
        }
}
    stage('pushImage'){
        steps{
            sh 'docker ps'
        }
    }
    }
}