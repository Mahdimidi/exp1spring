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
                sh "git clone https://github.com/Mahdimidi/exp1spring.git"
            }
        }
        stage ("Build") {
              steps {
                   dir("exp1spring"){
                      sh "mvn clean install"
                  }                
              }
          }
        stage ("SonarQube Analysis") {
            steps {
                withSonarQubeEnv('sonar-server'){
                    dir("exp1spring"){
                        sh 'mvn sonar:sonar'
                }                
            }
        }
    }
}
}
