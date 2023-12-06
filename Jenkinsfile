pipeline{
    agent any
    tools{
        maven 'MyMaven'
        dockerTool 'MyDocker'
    }
    stages{
        stage('git checkout'){
            steps{
                git url: 'https://github.com/999-andreas/springboot-rest-mysql.git'
            }
        }
        
        stage('Unit Test Execution'){
            steps{
                sh 'mvn test'
            }
        }
        
        stage('build the application'){
            steps{
                sh 'mvn clean install'
            }
        }
        
        stage('Build the docker image'){
            steps{
                sh 'docker build -t 999andreas/myrestapi ./docker'
            }
        }
        
        stage('Push to DockerHub'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
                    sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASS'
                    sh 'docker push 999andreas/myrestapi'
                }
            }
        }

        
        
    }
    post{
            failure{
                emailext body: 'Ce Build $BUILD_NUMBER a échoué',
                recipientProviders:[requestor()], subject: 'build', to:
                    'andreas.chatel5@gmail.com'
            }
        }
}
