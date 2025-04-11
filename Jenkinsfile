pipeline {
    agent {
        docker {
            image 'maven:3.8.8-openjdk-17'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Main') {
            steps {
                sh 'java -cp target/*.jar org.orlov.tom.Main || echo "Main не найден"'
            }
        }
    }
}
