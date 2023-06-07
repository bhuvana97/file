# file

https://archive.apache.org/dist/maven/maven-3/3.8.6/



pipeline {
  agent any
  stages {
    stage('Build Application') { 
      steps {
       echo 'Build Appplication...' 
        bat 'mvn clean install'
      }
    }
 	stage('Test') { 
      steps {
        echo 'Test Appplication...' 
        bat 'mvn test'
      }
    }
 	
   
	stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypointPlatform')
      }
            
      steps {
        echo 'Deploying only because of code commit...'
        echo 'Deploying to  dev environent....'
        bat 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -DworkerType=Micro -Dworkers=1 -Dregion=us-west-2'
      }
	  
	}
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
  }
}














mvn deploy -DmuleDeploy
<plugin>                 <groupId>org.apache.maven.plugins</groupId>                 <artifactId>maven-clean-plugin</artifactId>                 <version>3.0.0</version>             </plugin>             <plugin>                 <groupId>org.mule.tools.maven</groupId>                 <artifactId>mule-maven-plugin</artifactId>                 <version>${mule.maven.plugin.version}</version>                 <extensions>true</extensions>                 <configuration>                     <cloudHubDeployment>                         <uri>https://anypoint.mulesoft.com</uri>                         <muleVersion>${app.runtime}</muleVersion>                         <username>ravikumarmay2023</username>                         <password>Ravikumarmay2023</password>                         <applicationName>ravisapi</applicationName>                         <environment>Sandbox</environment>                         <region>us-east-1</region>                         <workers>1</workers>                         <workerType>MICRO</workerType>                     </cloudHubDeployment>                 </configuration>             </plugin>










