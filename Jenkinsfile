pipeline{
	agent any
	tools{
		maven 'maven'
	stages {
		stage ('Build') {
			steps{
					sh 'mvn clean package'
				}
		post {
			success {
				echo "Archiving the Artifacts"
				archiveArtifacts artifacts: '**/target/*.war'
			}
		}
		}
	stage ('Deploy to tomcat server') {
		steps{
		deploy adapters: [tomcat9(path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
	}
}
}
}
