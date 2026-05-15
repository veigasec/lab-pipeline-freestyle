pipeline {
    agent {
        label '(built-in)'
    }
    
    stages {               // conjunto de etapas
        stage('Nome') {    // uma etapa específica
            steps {        // ações dentro da etapa
                sh '''
                ls -la /var/jenkins_home
                '''
            }
        }
    }
}
