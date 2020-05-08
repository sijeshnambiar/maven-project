pipeline
{
agent any
stages
{
	stage ('source code checkout')
{
		steps
{
			git branch: 'master', url: 'https://github.com/sijeshnambiar/maven-project'
}
}
	stage ('compile source code')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn compile'
}
}			
}
	stage ('test source code')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn test'
}
}			
}
	stage ('build my package')
{
		steps
{
			withMaven(jdk: 'local_jdk', maven: 'local_mvn') 
{
				sh 'mvn package'
}
}			
}
	stage ('tomcat container')
{
		steps
{
			sshagent(['deploypackage']) 
{
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.32.126:/var/lib/tomcat/webapps'
}
}			
}
}
}
