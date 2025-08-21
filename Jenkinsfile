pipeline{
    agent any
    stages{
     stage('CodeScan'){
        steps{
            sh 'trivy fs . -o result.hcl' 
            sh 'cat result.hcl'
            
        }
    }
    stage('dockerLogin'){
        steps{
            sh 'aws ecr get-login-password --region us-east-1 |\
             docker login --username AWS \
             --password-stdin 515966507339.dkr.ecr.us-east-1.amazonaws.com'
        }
    }
    stage('dockerImageBuild'){
        steps{
            sh 'docker build -t jenkins-ci .'
        }
}
    stage('dockerImageTag'){
        steps{
            sh 'docker tag jenkins-ci:latest\
             515966507339.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
        }
    } 
    stage('pushImage'){
        steps{
            sh 'docker push\
             515966507339.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
        }
    }
    }

}