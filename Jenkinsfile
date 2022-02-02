//library 'pipeline'

//ejecucion.call()

pipeline {
    agent any
    environment {
        NEXUS_USER         = credentials('NEXUS-USER')
        NEXUS_PASSWORD     = credentials('NEXUS-PASS')
    }
    stages {
        stage("Pipeline"){
            steps {
                script{
                    stage("Paso 1: Build && Test"){
                        sh "echo 'Build && Test!'"
                        sh "gradle clean build"
                        // code
                    }
                }
            }
        }
    }
}