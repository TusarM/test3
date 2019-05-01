pipeline{
 agent any
 environment {
    ANYPOINT = credentials('ANYPOINT_CREDENTIALS')
 }
 stages {
 	stage ('Build'){
 		steps {
 			withMaven(maven:'maven'){
 				bat 'mvn -f mule-jenkins-pipeline/pom.xml clean install'
 			}
 		}
 	}
 	stage ('Deploy'){
 		steps {
 			withMaven(maven:'maven'){
 				bat 'mvn -f mule-jenkins-pipeline/pom.xml package deploy  -Dusername=$ANYPOINT_USR -Dpassword=$ANYPOINT_PSW -Denvironment=Development -DmuleDeploy'
 			}
 		}
 	}
 }

}
