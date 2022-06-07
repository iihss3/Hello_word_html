pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    tools {
        maven "Maven3"
   }
    environment {
        PATH = "C:/Users/ihssa/.jenkins/tools/hudson.tasks.Maven_MavenInstallation/Maven3/bin:$PATH";
    }
    stages {
        stage('build') {
            steps {
                //echo "Building the app...."
                bat 'C:/apache-maven-3.8.5-bin/apache-maven-3.8.5/bin/mvn.cmd clean install'
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
                bat 'C:/apache-maven-3.8.5-bin/apache-maven-3.8.5/bin/mvn.cmd test'
            }
        }
        stage('deploy') {
            steps {
                echo "deploying the app....."
                echo "deploying version ${params.VERSION}"
                bat "cd webapp/target"
                bat "copy webapp.war C:/Users/ihssa/OneDrive/Documents/apache-tomcat-10.0.21-windows-x64/apache-tomcat-10.0.21/webapps/"
            }
        }
    }
}            
