pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
        MONGO_URI = 'mongodb://admin:securepassword@mongodb-service.default.svc.cluster.local:27017' // Replace with your actual MongoDB connection string
    }

    stages {
        stage('SonarQube') {
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Deployment -Dsonar.ProjectName=Microservice_Deployment -Dsonar.java.binaries=.'''
                }
            }
        }
        stage('adservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/adservice/') {
                            sh "docker build -t adepeju/adservice:latest ."
                            sh "docker push adepeju/adservice:latest"
                            sh "docker rmi adepeju/adservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('cartservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/cartservice/src/") {
                            sh "docker build -t adepeju/cartservice:latest ."
                            sh "docker push adepeju/cartservice:latest"
                            sh "docker rmi adepeju/cartservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('checkoutservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/checkoutservice/") {
                            sh "docker build -t adepeju/checkoutservice:latest ."
                            sh "docker push adepeju/checkoutservice:latest"
                            sh "docker rmi adepeju/checkoutservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('currencyservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/currencyservice/") {
                            sh "docker build -t adepeju/currencyservice:latest ."
                            sh "docker push adepeju/currencyservice:latest"
                            sh "docker rmi adepeju/currencyservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('emailservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/emailservice/") {
                            sh "docker build -t adepeju/emailservice:latest ."
                            sh "docker push adepeju/emailservice:latest"
                            sh "docker rmi adepeju/emailservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('frontend') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/frontend/") {
                            sh "docker build -t adepeju/frontend:latest ."
                            sh "docker push adepeju/frontend:latest"
                            sh "docker rmi adepeju/frontend:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('loadgenerator') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/loadgenerator/") {
                            sh "docker build -t adepeju/loadgenerator:latest ."
                            sh "docker push adepeju/loadgenerator:latest"
                            sh "docker rmi adepeju/loadgenerator:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('paymentservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/paymentservice/") {
                            sh "docker build -t adepeju/paymentservice:latest ."
                            sh "docker push adepeju/paymentservice:latest"
                            sh "docker rmi adepeju/paymentservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('productcatalogservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/productcatalogservice/") {
                            sh "docker build -t adepeju/productcatalogservice:latest ."
                            sh "docker push adepeju/productcatalogservice:latest"
                            sh "docker rmi adepeju/productcatalogservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('recommendationservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/recommendationservice/") {
                            sh "docker build -t adepeju/recommendationservice:latest ."
                            sh "docker push adepeju/recommendationservice:latest"
                            sh "docker rmi adepeju/recommendationservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('shippingservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/shippingservice/") {
                            sh "docker build -t adepeju/shippingservice:latest ."
                            sh "docker push adepeju/shippingservice:latest"
                            sh "docker rmi adepeju/shippingservice:latest"
                            sh 'docker system prune -a -f --volumes'
                        }
                    }
                }
            }
        }
        stage('EKS-Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'myAppp-eks-cluster', contextName: '', credentialsId: 'k8s', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://074DE7A855880150B58EE4F2F9FB7503.sk1.us-east-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    }
}
