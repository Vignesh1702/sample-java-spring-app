pipeline {
    agent any
    stages{
        stage ("clone") {
            steps {
                git branch: 'main', url: 'https://github.com/Vignesh1702/sample-java-spring-app.git'
            }
        }
        stage ("build") {
            steps {
                sh "mvn clean install"
            }
        }
        stage ("docker image"){
            steps {
                sh "docker build -t java-image ."
                sh "docker images"
            }
        }
        stage("docker hub") {
            steps {
                sh "docker login -u gvignesh17 -p Vignesh!17021"
                sh "docker push gvignesh17/java-image"
            }
        }
        stage ("docker conatainer"){
            steps {
                sh "docker rm -f java-image"
                sh "docker run -d --name java-app -p 8087:8080 gvignesh17/java-image"
            }
        }
    }
}
