pipeline {
    agent any
    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }
    
    environment {
        SNAP_REPO = 'vprofile-snamshot'
		NEXUS_USER = 'admin'
		NEXUS_PASS = 'rdxx12rd'
		RELEASE_REPO = 'vprofile-release'
		CENTRAL_REPO = 'vpro-maven-central'
		NEXUSIP = '192.168.56.201'
		NEXUSPORT = '8081'
		NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post{
                success{
                    echo "yeaaa"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Test'){
            steps{
                sh 'mvn -s settings.xml test'
            }
        }
        stage('Check style analisis'){
            steps{
                sh 'mvn -s settings.xml checkstyle:ckeckstyle'
            }
        }
    }
}