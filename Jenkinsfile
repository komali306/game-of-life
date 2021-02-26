pipeline {
    agent { label 'ltecom'}
    parameters {
<<<<<<< HEAD
        string(name: 'MAVENGOAL', defaultValue: 'cleanpackage', description: 'Enter your maven goal')
=======
        string(name: 'MAVENGOAL', defaultValue: 'clean package', description: 'Enter your maven goal')
>>>>>>> 1d18f553a89c7fbce3a015834d4d518416c97770
    }
    triggers {
        upstream(upstreamProjects: 'gol-1', threshold: hudson.model.Result.SUCCESS)
        cron('H * * * 1-5')
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
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
        stage('post build') {
            steps {
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
            }
        }
    }    
}

