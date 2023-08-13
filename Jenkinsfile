
pipeline {
    triggers {pollSCM('*/2 * * * *')}
    agent any
    stages {
        stage ('Get or clone the code from repo') {
            steps {
                git branch: 'main', url: 'https://github.com/mmislamqa88/spring-petclinic.git'
            }
        }
        stage ('Building and Packaging code') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('Archiving Artifact'){
            steps{archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
                
            }
        }
        stage ('Displaying unit test results') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}