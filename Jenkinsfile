pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'mvn clean package'
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
        post{
            always{
            echo 'Saving artifacts..'
            archiveArtifacts artifacts: 'target/my.war', onlyIfSuccessful: true
            }
        }
        stage ('Deploy') {
            agent any
            steps{
                echo 'Deploying ......'
                sh 'asadmin --port 4848 deploy --force --name my --contextroot my target/my.war'
            }
        }
    }
}
