pipeline {
    
	agent any
	
	tools {
        maven "MAVEN3"
	jdk "OracleJDK8"	
    }
	
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "34.224.168.231:8081"
        NEXUS_REPOSITORY = "vprofile-release"
	NEXUS_REPOGRP_ID    = "vpro-maven-group"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
     stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
    
