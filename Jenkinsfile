pipeline {
    agent any

    stages {
        stage('1. Récupération du Code') {
            steps {
                checkout scm
                echo '✅ Code récupéré avec succès depuis GitHub !'
            }
        }
        
        stage('2. Construction (Image Docker)') {
            steps {
                echo '⚙️ Lancement de la construction de l\'image Docker...'
                // La commande "sh" permet à Jenkins d'exécuter des commandes Linux
                sh 'docker build -t vampi-sec:latest .'
                echo '✅ Image Docker construite avec succès !'
            }
        }
        
        stage('3. Analyse de Sécurité (Placeholders)') {
            steps {
                echo '🛡️ C\'est ici que nous ajouterons les scans Trivy et ZAP.'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Le build a réussi ! L\'image est prête.'
        }
        failure {
            echo '❌ Échec. Il faut vérifier les logs de la console Jenkins.'
        }
    }
}
