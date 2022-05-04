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
                    '''
                }
            }

            stage ('Build') {
                steps {
                    sh '''
                        echo "Building $MODULE"
                        mvn -pl $MODULE clean compile --also-make
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