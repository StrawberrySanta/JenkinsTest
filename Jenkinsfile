pipeline {
    agent any

    environment {
        MAVEN_IMAGE = 'maven:3.8.8-openjdk-17'
    }

    stages {
        stage('Clone') {
            steps {
                echo 'Клонируем репозиторий'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Собираем проект через Docker Maven'
                script {
                    docker.image("${MAVEN_IMAGE}").inside {
                        sh 'mvn clean package'
                    }
                }
            }
        }

        stage('Run Main') {
            steps {
                echo 'Запускаем Main (если есть)'
                script {
                    docker.image("${MAVEN_IMAGE}").inside {
                        // Подстрой под свой путь
                        sh 'java -cp target/*.jar org.orlov.tom.Main || echo "Main не найден"'
                    }
                }
            }
        }
    }
}
