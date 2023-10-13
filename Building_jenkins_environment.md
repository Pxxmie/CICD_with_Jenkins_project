# Building Jenkins Environment 

Once the Jenkins server is set up, you'll need to configure it to suit your specific needs, such as installing plugins, configuring security settings, setting up SSH keys etc. 
.

- Now that our Jenkins is up and running in our EC2 build environment. We can access via web through our EC2 public ip and jenkins port. 
This is the page we should see. 

  <img src="images/unlock_jenkins_page.png" width="800" height="600">

- We can access the password through our gitbash terminal by running this command: 

   ```bash
   ubuntu@ip-10-0-2-137:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   ```
- After entering your passsword. You should see Customize Jenkins page, select **Install suggested plugins**. 
  
   <img src="images/customise_jenkins.png" width="600" height="500">

   <img src="images/getting_started_page.png" width="600" height="500">

- It should then prompt us to add the following details, enter details in the field followed by **save and continue**.
  
  <img src="images/admin_user.png" width="400" height="400">

- At this point you should be able to see the following page: Jenkins home page.
  
  <img src="images/jenkins_page.png" width="700" height="400">


## Install Jenkins Plugins

- We will need to add some plugins, in order to build our first job successfully.  
   - **Nodejs** - This enables Jenkins to execute Node.js scripts. 
   - **Office 365 connector (Webhook)** - allows Jenkins to receive notifications from other systems (GitHub), this enables Jenkins to trigger jobs. 
   - **SSh agent** - allows you to use a specific SSH key for authentication when connecting to remote servers in your Jenkins jobs.
  
- At the Jenkins home page on the left hand select Manage Jenkins -> Manage Plugins select the tab Available and search for the following plugin followed by the ones listed above:

  ![Alt text](images/plugin_nodejs.png) 

  ## Configuring Plugins

  When you install plugins like NodeJS in Jenkins, you typically need to configure them before you can use them in your Jenkins jobs. 

- Go to "manage jenkins" on the side bar and select **Tools**. 

   ![Alt text](images/manage_tools.png)

- Scroll down to **NodeJS installations** and select **Add NodeJS**

  ![Alt text](images/add_nodejs.png)

- Give it a name i.e *tech254-app-deployment* and under Version, since my app.js only supports version 13 and under, I have selected **NodeJS 12.0.0**. Finally, save your settings. 
  
   ![Alt text](images/node_js_settings.png)

 - When you create a job, in the build step where you want to use NodeJS, you'll find an option to "Provide Node & npm bin/ folder to PATH". Enable this option.

   From the "NodeJS Installation" dropdown, select the installation you configured earlier (e.g., "tech254-app-deployment"). This ensures that the specified NodeJS version is used for that specific job. 

   ![Alt text](images/select_node_added.png)

   