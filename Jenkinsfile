pipeline {
    agent { label 'ltecom'}
    parameters {
        string(name: 'MAVENGOAL', defaultValue: 'clean package', description: 'Enter your maven goal')
    }
    triggers {
   
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

