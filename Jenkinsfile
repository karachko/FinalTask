pipeline {
    agent any
    tools { 
        maven 'maven363'
        jdk 'jdk8'
    }
    stages {
        stage('Clonning repo from Git hub') {
            steps {
                git 'https://github.com/wyona/spring-boot-hello-world-rest'
                
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('Publishing site on the Docker-Web') {
            steps {
                            
                sshPublisher(publishers: [sshPublisherDesc(configName: 'Docker', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ls -la', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/home/student/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
                
    }
}
