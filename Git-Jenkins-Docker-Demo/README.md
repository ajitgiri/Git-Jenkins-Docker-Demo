# Git, Jenkins, Docker
==============================

This is a Simple project and will used to practice the Git, Jenkins and Docker

	1. Pushed to to the Git Repository
	2. Integrate with Jenkins
	3. Using Jenkins will build Docker Image and push to the Doker Hub 

Changed the server port to 8000 as in my local Jenkin is running in port 8080 

	server.port = 8000
		
1.Create and Integrate Git with Eclipse and GitHub: https://www.youtube.com/watch?v=zVX7H67nLOM

=====================================
	  
	  1. Create a repository in GitHub
	  2. Create Project in Eclise/STS
	  3. Create Local git repository before push to GitHub as below:
			i. Right click on project -> Team  -> Share Project
			ii. Select : Use Or create repository in parent folder of project
			iii.Select the Check box showing the local path of the project
			iv. Click on "Create Repository"
			v.  Click on Finish 
	  4. Open GitStagging : Commit files to the Local repository before pushing to remote Master Repository
			i. select all files from UnStagged Changes -> Staged Changes 
			ii. Add Comment on "Commit Changes" Section
			iii. Click on Commit ; If asked than provide the credentials for GitHub repository
	  5. Finally Push the Project to the GitHub Repository
			i. Right click on the project -> Team -> Remort ->Push 
			ii. Provide the GitHub repository cloned URL and Credentials
			iii.Folow the steps
			
	Process:2
	=======
		1. Create Repository in Github account
		2. Create project in Eclipse
		3. Start Eclipse and follow the below steps
			i. Go to Prospective -> Search for Git Repositories 
			ii. Click on Clone and add Repository button
			iii. Click on Clone URI and past the URL you copied of created Repository from GitHub 
		4. Right click on the project, created on Eclipse
			i. Go to Team
			ii. Share project
			iii. Select the repository created in Step 3.
			iv. Finish
		5. Now able to see the marks and can commit the files from the created project in Eclipse 

Now Build the Docker Image in Local and Test
	
		1. Need to add the run the created project and test; whether it's working properly or not
		2. To create the Docker image follow below steps
			i. Add Maven build plugin to pom.xml
			ii.Configure the Dockerhub repository with Tag Name
			iii. Right click on Project 
					Run As -> Maven Build -> package -> Apply -> Run
			
			ERROR: Build will fail with Below Error:
			
			[INFO] Path(dockerfile): null
			[INFO] Path(contextDirectory): C:\Users\agiri20\git\Git-Jenkins-Docker-Demo\Git-Jenkins-Docker-Demo
			[ERROR] Missing Dockerfile in context directory: C:\Users\agiri20\git\Git-Jenkins-Docker-Demo\Git-Jenkins-Docker-Demo
			[INFO] ------------------------------------------------------------------------
			[INFO] BUILD FAILURE
			[INFO] ------------------------------------------------------------------------
			[INFO] Total time: 20.834 s
			[INFO] Finished at: 2020-01-31T09:31:24+05:30
			[INFO] Final Memory: 44M/289M
			[INFO] ------------------------------------------------------------------------
			[ERROR] Failed to execute goal com.spotify:dockerfile-maven-plugin:1.4.10:build (default) on project Git-Jenkins-Docker-Demo: Missing Dockerfile in context directory: C:\Users\agiri20\git\Git-Jenkins-Docker-Demo\Git-Jenkins-Docker-Demo -> [Help 1]
			[ERROR] 
			[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
			[ERROR] Re-run Maven using the -X switch to enable full debug logging.
			[ERROR] 
			[ERROR] For more information about the errors and possible solutions, please read the following articles:
			[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
			
	# ** To Solve this issue, need to create and place the Dockerfile in project root directory
			
		Now build the application
		 > mvn package
			 
	  FAILED : Connect to localhost:2375 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect
			 
	#** To solve this need to install the Docker in the system and start it, than try same 
		Now build the application
		 > mvn package
			
		It will build the Jar and Image file for this project
			