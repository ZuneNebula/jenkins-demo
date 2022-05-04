pipeline {
    agent any
    tools {
        maven 'MAVEN'
        jdk 'JAVA_HOME'
    }
     stages {
            stage ('Initialize') {
                steps {
                    sh '''
                        echo "PATH = ${PATH}"
                        echo "M2_HOME = ${M2_HOME}"
                        echo "JAVA_HOME" = $ {JAVA_HOME}"   "
                    '''
                }
            }

            stage ('Build') {
                steps {
                    sh '''
                        echo "Building $MODULE"
                        mvn -B -DskipTests clean package
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