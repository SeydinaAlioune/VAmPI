pipeline {
    agent any

    stages {
        stage('1. Récupération du Code') {
            steps {
                checkout scm
                echo '✅ Code récupéré avec succès.'
            }
        }
        
        stage('2. Construction (Image Docker)') {
            steps {
                sh 'docker build -t vampi-sec:latest .'
                echo '✅ Image Docker construite.'
            }
        }
        
        stage('3. Scan de Sécurité (Trivy)') {
            steps {
                echo '🛡️ Lancement du scan avec Trivy...'
                // On utilise le conteneur Trivy pour scanner l'image locale
                // --exit-code 1 : Arrête le pipeline si une faille CRITIQUE ou HIGH est trouvée
                sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy image --exit-code 1 --severity HIGH,CRITICAL vampi-sec:latest'
                echo '✅ Scan terminé avec succès.'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Pipeline réussi et image sécurisée !'
        }
        failure {
            echo '❌ Le build a échoué (Soit erreur Docker, soit Trivy a trouvé des failles !)'
        }
    }
}
