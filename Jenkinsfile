pipeline {
    agent any
    stages {
        stage('run frontend') {
            steps {
                echo "excuting yarn..."
                Nodejs('NodeJS 10.17.0') {
                    sh 'yarn install'
                }
            }
        }
        stage('run backend') {
            steps {
                echo "excuting gradle..."
                withgradle(){
                    sh './gradlew -v'
                }
            }
        }
    }
}
