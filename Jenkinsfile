pipeline {
    agent { label 'ltecom'}
    triggers {
        upstream(upstreamProjects: 'golnightbuild', threshold: hudson.model.Result.SUCCESS)
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

