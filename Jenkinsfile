pipeline {
    agent { label 'ltecom'}
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
<<<<<<< HEAD
=======

>>>>>>> 6bd57de242467770713131f12e093f8442294195
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
>>>>>>> 6bd57de242467770713131f12e093f8442294195
