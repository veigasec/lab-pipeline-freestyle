pipeline {
    agent any
    
    options {
        timeout(time: 10, unit: 'MINUTES')
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    
    environment {
        APP_NAME = 'minha-app'
        VERSION  = "1.0.${BUILD_NUMBER}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo "Iniciando build de ${APP_NAME} versão ${VERSION}"
                echo "Executando no agente: ${env.NODE_NAME}"
            }
        }
        
        stage('Build') {
            steps {
                sh '''
                    echo ">> Compilando aplicação..."
                    mkdir -p build
                    echo "binário simulado" > build/app.bin
                    sleep 2
                '''
            }
        }
        
        stage('Test') {
            steps {
                sh '''
                    echo ">> Executando testes..."
                    sleep 2
                    echo "Todos os testes passaram!"
                '''
            }
        }
        
        stage('Package') {
            steps {
                sh '''
                    echo ">> Empacotando artefato..."
                    tar -czf build/app-${VERSION}.tar.gz build/app.bin
                    ls -lh build/
                '''
            }
        }
        
        stage('Deploy') {
            when {
                branch 'main'   // só executa se estiver na branch main
            }
            steps {
                echo ">> Deploy simulado para produção..."
            }
        }
    }
    
    post {
        always {
            echo "Pipeline finalizado com status: ${currentBuild.currentResult}"
            archiveArtifacts artifacts: 'build/*.tar.gz', allowEmptyArchive: true
        }
        success {
            echo "Build #${BUILD_NUMBER} concluído com sucesso!"
        }
        failure {
            echo "Build #${BUILD_NUMBER} falhou. Verifique os logs."
        }
    }
}
