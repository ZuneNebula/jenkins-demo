pipeline {
    agent any
    tools {
        maven 'Maven'
        jdk 'Jdk'
    }
     stages {
            stage ('Initialize') {
                steps {
                    sh '''
                        echo "PATH = ${PATH}"
                        echo "M2_HOME = ${M2_HOME}"
                    '''
                }
            }

            stage ('Build') {
                steps {
                    sh '''
                        echo "Building $MODULE"
                        mvn clean package
                    '''
                }
                post {
                    success {
                        junit 'target/surefire-reports/**/*.xml'
                    }
                }
            }
     }
}