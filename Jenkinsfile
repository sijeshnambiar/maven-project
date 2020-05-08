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
				sh 'mvn packgae'
}
}			
}
}
}
