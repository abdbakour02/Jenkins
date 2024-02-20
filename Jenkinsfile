pipeline {
    agent any
    tools {
        gradle 'Gradle'
    }
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
                    sh './gradlew -v'
            }
        }
    }
}
