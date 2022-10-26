pipeline {
    
	agent any
	
	tools {
        maven "MAVEN3"
	jdk "OracleJDK8"	
    }
	
    environment {
        NEXUS_VERSION = "nexus3"
	SNAP_REPO = "vprofile-snapshot"
	CENTRAL_REPO = "vpro-maven-central"
	RELEASE_REPO = "vprofile-release"
        NEXUS_USER = "admin"
	NEXUS_PASS = "199310"
        NEXUS_PROTOCOL = "http"
        NEXUSIP = "23.20.77.244"
	NEXUSPORT = "8081"
	NEXUS_GRP_REPO = "vpro-maven-group"
        NEXUS_REPOSITORY = "vprofile-release"
	NEXUS_REPOGRP_ID    = "vpro-maven-group"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
     stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml install -DskipTests'
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
	


