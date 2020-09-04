pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'mvn clean package'
            }
            post{
                always{
                echo 'Saving artifacts..'
                archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
                }
            }
        }
      /*   stage('Test') {
            steps {
                echo 'Testing..'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
                sh "mvn run"
        } */

        stage ('Deploy') {
            agent any
            steps{
                echo 'Deploying ......'
                sh 'asadmin --port 4848 deploy --force --name springMVC-1.0-SNAPSHOT --contextroot springMVC-1.0-SNAPSHOT target/springMVC-1.0-SNAPSHOT.war'
            }
        }
    }
}
