pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
		
		//Stage 3 publish artifact to nexus
		
		stage('Publish to Nexus') {
			steps {
				nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.8-SNAPSHOT.war', type: 'war']], credentialsId: '504132c5-3750-4671-bb11-690ec25ac2e5', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.113:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'DevOpsLab-SNAPSHOT', version: '0.0.8-SNAPSHOT'
			}
		}
		
        // Stage3 : Publish the source code to Sonarqube
        //stage ('Sonarqube Analysis'){
        //    steps {
        //        echo ' Source code published to Sonarqube for SCA......'
        //        withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
        //             sh 'mvn sonar:sonar'
        //        }

        //   }
        //}

        
        
    }

}