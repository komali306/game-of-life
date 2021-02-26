pipeline {
    agent { label 'ltecom'}
    triggers {
        cron('H * * * 1-5')
    }
    stages {
        stage('scm') {
            steps {
                git 'https://github.com/komali306/game-of-life.git'
            }
        }
        stage('build') {
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage('postbuild') {
            steps {
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
            }
        }
    }    
}
<<<<<<< HEAD

=======
>>>>>>> 696a2ae902d2dcd4769ba3a2bb80681c6bc8c511

