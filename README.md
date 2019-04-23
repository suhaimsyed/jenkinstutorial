# jenkinstutorial

Prerequisite

1. installation of docker
2. creating an account in https://hub.docker.com/


Steps to perform
1.	Navigate to the root folder 
2.	Enter docker-compose up
3.  Access localhost or localhost:80
4.  Enter the password provided to you in the log or console when asked for on jenkins

```
jenkins_1  | *************************************************************
jenkins_1  | *************************************************************
jenkins_1  | *************************************************************
jenkins_1  | 
jenkins_1  | Jenkins initial setup is required. An admin user has been created and a password generated.
jenkins_1  | Please use the following password to proceed to installation:
jenkins_1  | 
jenkins_1  | XXXXXXXX
jenkins_1  | 
jenkins_1  | This may also be found at: /var/jenkins_home/secrets/initialAdminPassword
jenkins_1  | 
jenkins_1  | *************************************************************
jenkins_1  | *************************************************************
jenkins_1  | *************************************************************
```

5. Select "Install suggested plugins"
6. Create Admin user with the relevant details
7. Proceed to start using jenkins

Before Creating a new Project
1. Navigate to Manage Jenkins -> Global Tool configuration and add JDK , Maven etc to install automatically
2. Create an account in oracle `https://login.oracle.com/oaam_server/login.do`
3. Provide the credentials in jenkins for JDK installation

Create a new Project
1. Create new maven project
2. Enter the name
3. Provide a git URL - `https://github.com/suhaimsyed/graphqltutorial.git` in scm of your choice
4. Add root pom.xml in build section
5. Build the project

Export the project to dsl
1. Click on the export xml to dsl from the jenkins homepage

Make changes to the dsl 
```
mavenJob('dsl2') {
    scm {
		git {
			remote {
				github("suhaimsyed/graphqltutorial", "https")
			}
			branch("*/master")
		}
	}
    goals('clean verify')
}
```

Execute the dsl as a build task

A new Job will be created with dsl2 as name

Execute the job and see the result

  
