pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_8_1') {
                    bat 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    bat 'cf login -a http://api.run.pivotal.io -u shashankk197@gmail.com -p Thanos2021!'
                    bat 'cf push'
                }
            }

        }

    }

}
