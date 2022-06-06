pipeline {
//    agent any
//    parameters {
//        choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: '')
//        booleanParam(name: 'executeTests', defaultValue: true, description: '')
//    }
//    tools {
//        maven "Maven3"
//   }
    stages {
        stage('build') {
            steps {
                //echo "Building the app...."
                sh "mvn clean install"
            }
        }
        stage('test') {
            when {
                expression {
                    params.executeTests == true 
                }
            }           
            steps {
                echo "Testing the app..."
                //sh "mvn test"
            }
        }
        stage('deploy') {
            steps {
                echo "deploying the app....."
                echo "deploying version ${params.VERSION}"
                sh "cd webapp/target"
                sh "copy webapp.war C:/Users/ihssa/OneDrive/Documents/apache-tomcat-10.0.21-windows-x64/apache-tomcat-10.0.21/webapps/"
            }
        }
    }
}            
