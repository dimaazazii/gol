//Start the pipeline 
pipeline{
	//Where the pipeline job will run
	agent{
		label "Windows_Slave_01"
	}
	
	//Start of the stages: build, test,deploy ...
	stages{
	
		//Start of the Build stage
		stage('build'){
			
			//Start of the steps to run inside the Build stage
			steps{
			
				//Build with Maven
				bat 'mvn clean install'
			}
		}
		stage('deploy'){
			steps{
				bat 'sc stop Tomcat7'
				bat 'ping 127.0.0.1 -n 6'
				
				bat 'xcopy /y "C:\\temp\\CICD Setup\\Jenkins_Slave\\workspace\\GOL_Pipleine\\gameoflife-web\\target\\gameoflife.war" "C:\\temp\\CICD Setup\\Tomcat 7.0\\webapps"'
				
				bat 'sc start Tomcat7'
			}
		}
	}
}
