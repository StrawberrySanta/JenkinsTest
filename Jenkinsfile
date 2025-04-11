pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Клонируем репозиторий'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Собираем проект'
                sh 'mvn clean package'
            }
        }
        stage('Test Run') {
            steps {
                echo 'Запускаем Main'
                sh 'java -cp target/*.jar org.example.Main'
            }
        }
    }
}
