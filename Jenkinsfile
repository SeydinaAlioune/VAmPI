pipeline {
    agent any

    stages {
        stage('1. Récupération du Code') {
            steps {
                // Cette commande télécharge automatiquement le code depuis ton GitHub
                checkout scm
                echo '🚀 ALERTE : Déclenchement automatique réussi !!!'
            }
        }
        
        stage('2. Construction (Préparation)') {
            steps {
                echo '⚙️ C\'est ici que nous construirons l\'image Docker de l\'application plus tard.'
            }
        }
        
        stage('3. Analyse de Sécurité (Placeholders)') {
            steps {
                echo '🛡️ C\'est ici que nous ajouterons les scans Trivy, SonarQube et ZAP.'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Le pipeline de base fonctionne ! Bientôt, Jenkins t\'enverra un mail ici.'
        }
        failure {
            echo '❌ Aïe, le pipeline a échoué. Il faut vérifier les logs.'
        }
    }
}
