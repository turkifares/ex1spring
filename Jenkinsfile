pipeline {
    agent any 
    tools { 
        maven 'maven'
    }
    stages {
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
                   dir("exp1spring"){
                      sh "mvn clean install"
                      sh "docker build -t docexp1-spring ."
                  }                
              }
          }
        stage ("Run docker compose") {
            steps {
                 dir("exp1-spring"){
                    sh " docker compose up -d"
                }                
            }
        }
    }
}
