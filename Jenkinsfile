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
                        sh "mvn clean compile -e"
                        // code
                    }
                    stage("Paso 2: Testear"){
                        sh "echo 'Test Code!'"
                        // Run Maven on a Unix agent.
                        sh "mvn clean test -e"
                    }
                    stage("Paso 3: Build .Jar"){
                            sh "echo 'Build .Jar!'"
                            // Run Maven on a Unix agent.
                            sh "mvn clean package -e"
                    }
                    stage("Paso 4: Análisis SonarQube"){
                        steps {
                            withSonarQubeEnv('sonarqube') {
                                sh "echo 'Calling sonar Service in another docker container!'"
                                // Run Maven on a Unix agent to execute Sonar.
                                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=laboratorioM3-sonar'
                            }
                        }
                        // post {
                        //     //record the test results and archive the jar file.
                        //     success {
                        //         //archiveArtifacts artifacts:'build/*.jar'
                        //         nexusPublisher nexusInstanceId: 'nexus',
                        //         nexusRepositoryId: 'devops-usach-nexus',
                        //         packages: [
                        //             [$class: 'MavenPackage',
                        //             mavenAssetList: [
                        //                 [classifier: '',
                        //                 extension: '.jar',
                        //                 filePath: 'build/DevOpsUsach2020-0.0.1.jar']
                        //                 ],
                        //                 mavenCoordinate: [
                        //                     artifactId: 'DevOpsUsach2020',
                        //                     groupId: 'cl.devopsusach2020',
                        //                     packaging: 'jar',
                        //                     version: '0.0.1-feature-nexus']
                        //             ]
                        //         ]
                        //     }
                        // }
                    }
                    // stage("Paso 4: Subir Nexus"){
                    //     nexusPublisher nexusInstanceId: 'nexus',
                    //     nexusRepositoryId: 'devops-usach-nexus',
                    //     packages: [
                    //         [$class: 'MavenPackage',
                    //             mavenAssetList: [
                    //                 [classifier: '',
                    //                 extension: 'jar',
                    //                 filePath: 'build/libs/DevOpsUsach2020-0.0.1.jar'
                    //             ]
                    //         ],
                    //             mavenCoordinate: [
                    //                 artifactId: 'DevOpsUsach2020',
                    //                 groupId: 'com.devopsusach2020',
                    //                 packaging: 'jar',
                    //                 version: '0.0.1'
                    //             ]
                    //         ]
                    //     ]
                    // }
                    // stage("Paso 4: Análisis SonarQube"){
                    //     steps {
                    //         withSonarQubeEnv('sonarqube') {
                    //             sh "echo 'Calling sonar Service in another docker container!'"
                    //             // Run Maven on a Unix agent to execute Sonar.
                    //             sh 'mvn clean verify sonar:sonar'
                    //         }
                    //     }
                    //     post {
                    //         //record the test results and archive the jar file.
                    //         success {
                    //             //archiveArtifacts artifacts:'build/*.jar'
                    //             nexusPublisher nexusInstanceId: 'nexus',
                    //             nexusRepositoryId: 'devops-usach-nexus',
                    //             packages: [
                    //                 [$class: 'MavenPackage',
                    //                 mavenAssetList: [
                    //                     [classifier: '',
                    //                     extension: '.jar',
                    //                     filePath: 'build/DevOpsUsach2020-0.0.1.jar']
                    //                     ],
                    //                     mavenCoordinate: [
                    //                         artifactId: 'DevOpsUsach2020',
                    //                         groupId: 'cl.devopsusach2020',
                    //                         packaging: 'jar',
                    //                         version: '0.0.1-feature-nexus']
                    //                 ]
                    //             ]
                    //         }
                    //     }
                    // }
                }
            }
        }
    }
}