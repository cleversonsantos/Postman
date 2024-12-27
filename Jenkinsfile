pipeline {
    agent none

    options {
        buildDiscarder(logRotator(numToKeepStr: '30'))
        timestamps()
    }

    stages {
        stage('top') {
            parallel {
                stage('v0.10.48-zone') {
                    agent {
                        label joyCommonLabels(image_ver: '15.4.1')
                    }
                    tools {
                        nodejs 'sdcnode-v0.10.48-zone'
                    }
                    stages {
                        stage('check') {
                            steps{
                                sh('make check')
                            }
                        }
                        stage('test') {
                            steps{
                                sh('make test')
                            }
                        }
                    }
                }

                stage('v4-zone') {
                    agent {
                        label joyCommonLabels(image_ver: '15.4.1')
                    }
                    tools {
                        nodejs 'sdcnode-v4-zone'
                    }
                    stages {
                        stage('check') {
                            steps{
                                sh('make check')
                            }
                        }
                        stage('test') {
                            steps{
                                sh('make test')
                            }
                        }
                    }
                }

                stage('v6-zone64') {
                    agent {
                        label joyCommonLabels(image_ver: '18.4.0')
                    }
                    tools {
                        nodejs 'sdcnode-v6-zone64'
                    }
                    stages {
                        stage('check') {
                            steps{
                                sh('make check')
                            }
                        }
                        stage('test') {
                            steps{
                                sh('make test')
                            }
                        }
                    }
                }

                // Adicione uma nova etapa para executar os testes do Postman com Newman
                stage('Executar Testes Postman') {
                    agent any
                    steps {
                        script {
                            // Instalar o Newman
                            sh 'npm install -g newman'

                            // Executar o Newman para rodar os testes com o arquivo de ambiente que contém o token JWT
                            sh 'newman run ServeRest_API.postman_collection.json -e Serverest.postman_environment.json'
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            joySlackNotifications()
        }
    }
}
 