# CI/CD (Continuous Integration and Continuous Delivery/Deployment)

## What is CICD?

CI/CD is considered to be the backbone of DevOps practices and automations.

Continuous Delivery is an extension to continous intergration which helps in ensuring that the new releases can get to customers faster in a sustainable way. Additionally, Contionous Deployment is one more step to continuous delivery whhich helps to ensure that every changes made passes all the stages of the production pipleline to be released to the customers. No human intervention required.



## Why Jenkins?

Jenkins is a open source automation server in which the central build and CI process can take place. It is a java-based program. Free with lots of dependecies making it easier to use. The plugins are powerful and easy to use. 

## Other tools that can be used for CICD

- Gitlab CI/CD
- Travis CI
- CircleCI
- Azure DevOps

## Why build a pipeline?
- Automation and Efficiency
- Faster Time to market
- Saves time (3 days work to be done in 3 minutes)


## Business value?
- Faster time to market.
- Improved Software Quality
- Scalability
- Efficieny and productivity
- Saves Cost (making it profitable)
  
# Architecture of Software Development Lifecycle

  Plan -> Design -> Develop -> Test -> Deploy


1. The code is initially stored on a local 

2. A pair of SSH keys is generated and one key (public) is added to the GitHub account this helps in connecting with GitHub. 

3. A webhook is set up, which automates the process of pushing code to the next stage whenever changes are made locally.Using webhook takes away the need for manual commands.

4. An SSH key is generated on GitHub and linked to Jenkins.

5. The code is tested, specifically by adding a payment gateway to ensure it functions correctly.

6. A master node is used to conduct automated tests before moving the code into production.

7. An agent node is employed in the testing process working with master node.

8. If the tests pass successfully, the code is pushed to the production. However, if the tests fail, the code is sent back to the CI stage for further planning and designing and building.

9. The code is then deployed to an EC2 instance on AWS using SSH. Port 22 is used for SSH communication.
![Alt text](CICD.images/CICD.png)

# How to build project on Jenkins;

1. Log in to Jenkins.
   
2. Go to New Item.
   
3. Enter the item name (larish-testing-env)
   
4. Then select freestyle project and select ok.
   
5. Select discard old builds and for max number of   build put 3 as shown in the image.

![Alt text](<CICD.images/Jenkins 1.png>)

6. Then go to build option and select execute shell and on description write a linux command. For example I put uname which will give the name of operating system I am using. 

![Alt text](<CICD.images/build jenkins.png>)

7. Then select save.
  
8. Then go to build now.

![Alt text](CICD.images/build.now.jenkins.png)

9. On build history select the arrow down and select console output.

![Alt text](<CICD.images/console output.png>)

![Alt text](<CICD.images/outup info.png>)


# How to add webhook

1. Go to your repository and select webhook.
    
![Alt text](<CICD.images/webhook selection.png>)

1. select add webhook.

2. add the payroll url, content type.
   
![Alt text](CICD.images/webhook.png) 

1. Go to Which events would you like to trigger this webhook and select the option "let me select individual event". Select pull requests and push.
   
![Alt text](<CICD.images/webhook options.png>)  

1. Select Active and Add webhook. 

# Steps to connect github and jenkins

1. Log in to Jenkins and navigate to the Jenkins Dashboard.

2. nter a name for the job and select "Freestyle project," then click "OK."
   
3. Select github project and enter the github http linke from code. 
   
![Alt text](<CICD.images/github url.png>)
   
4. Restrict where this project can be run and on label expression as sparta-ubuntu-node.


5. In source code select git and paste the SSH link of your GitHub repository in the provided field.

6. Add a private SSH key by clicking on the "Add" button and providing the appropriate key. Make sure the file name matches the private key file.

7. Change the branch to "main" (or your preferred branch name) in the branch specifier field.

8. In the "Build Environment" section, select "Provide Node & npm bin/ folder to PATH" and choose "Sparta-Node-JS" from the dropdown menu.
  
![Alt text](CICD.images/node.png)
   
9.  Click on "Add build step" and select "Execute shell" from the dropdown and add commands. 

![Alt text](CICD.images/build.png)
   
10. Click on "Build Now" to initiate the build process.


# How to build a project on jenkins;

1. Plan the artitechture 
2. Divide the jobs to different parts to break it down.

# Job 1: Test on dev 

1. This tests for the npm install. 

# job 2: This part is to merge dev to main branch

1. First create a dev branch on github and make a change on dev branch and push the commit.
2. If the test pass then code should merge from dev to main branch.

# job 3: Copy the app to push to production. 

1. SSH into the EC2 instance.
2. Navigate to the app folder
3. npm install
4. pm2 kill
5. pm2 start app.js

# Commands use  for job 3:

#to copy the app folder
rsync -avz -e "ssh -o StrictHostKeyChecking=no" app ubuntu@ec2-54-74-90-137.eu-west-1.compute.amazonaws.com:/home/ubuntu/app
# SSH key
ssh -o StrictHostKeyChecking=no ubuntu@ec2-54-74-90-137.eu-west-1.compute.amazonaws.com <<EOF
    # Navigate to app folder
    cd app
    pm2 kill
    pm2 start app.js




