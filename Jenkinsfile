pipeline {
    agent any 
    tools { 
        maven 'maven'
    }
    stages {
        stage('Reload Configuration') {
      steps {
        reload()
      }
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/turkifares/ex1spring.git"
            }
        }
        stage ("Generate backend image") {
              steps {
                   dir("ex1-spring"){
                       withMaven(maven: 'MVN'){
                           sh "mvn clean install"
                       }
                      
                      sh "docker build -t docexp1-spring ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("ex1-spring"){
                    sh " docker compose up -d"
                }                
            }
        }
    }
}
