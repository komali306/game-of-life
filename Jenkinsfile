pipeline {
    agent { label 'ltecom'}
    parameters {
        string(name: 'MAVENGOAL', defaultvalue: 'cleanpackage', description: 'Enter your maven goal')
    }
    triggers {
        upstream(upstreamProjects: 'gol-1', threshold: hudson.model.Result.SUCCESS)
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
                sh script: "mvn ${params.MAVENGOAL}"
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

