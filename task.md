# CICD Pipeline

What is CICD?

Continous Integration and Continous Delivery. 

CI (Continuous Integration):
CI is like a team collaboration. Whenever someone on the team makes a code change, they immediately share it with everyone else. This ensures that everyone is working with the latest code and any issues are caught early. It involves automating the process of building and testing code changes.

CD (Continuous Delivery) and CDE (Continuous Deployment):
CD takes CI a step further by automatically preparing the code for release. It includes tasks like packaging the code, deploying it to the specific environments (e.g., staging, production), and running additional tests. CDE goes even further and automatically deploys the code to production without manual intervention.

Key difference: CD makes sure the code is ready for release, while CDE actually puts the code into production.

![Alt text](<CICD.images/CICD diagram.png>)
The CI/CD pipeline is all about automation: Initiating code builds, automated testing, and automated deploying to the staging or production environments. 

# Git Workflow
![Alt text](<CICD.images/Git workflow.jpg>)

1. Work: Make changes to the files in your local repository according to your development requirements. You can create, modify, or delete files.

2. Add: Select the specific changes you want to include in the next commit using the git add . command. 

3. Commit: Create a new commit with a message using the git commit -m "" command. This saves your changes and creates a new commit ready for the push

4. Push: Push your local commits to the remote repository using the git push -u command. This updates the remote repository with the latest changes.

# What is Jenkins and why jenkins?

Jenkins is open source automates repetitive tasks in software development. It provides a user-friendly website where you can define and schedule jobs. These jobs can build, test, and deploy your code automatically. Jenkins integrates with tools like Git and has lots of plugins to customize its behavior.

# Benefits of Jenkins

efits of using Jenkins:

1. Automation: Jenkins saves time and effort by automating tasks that would otherwise be done manually.

2. Integration: It works well with different tools and technologies commonly used in development.

3. Extensibility: Jenkins can be customized using various add-ons to fit your project's needs.

4. Scalability: It can handle large projects with many developers and multiple jobs running at the same time.

5. Visibility: Jenkins provides clear reports and notifications so you can easily see the progress and any issues.

# Jenkins workflow

1. Developers write and save their code changes in a code repository (like Git).

2. Jenkins detects the changes and starts a build process, which compiles the code and runs automated tests.
   
3. If the build and tests are successful, Jenkins deploys the code to a testing environment.
   
4. esters run additional tests to ensure the code works as expected.
   
5. If all tests pass, Jenkins can deploy the code to a production environment.

# SDLC (Software Development Life Cycle) Workflow Stages:

1. Requirements gathering: Understand and document what the software needs to do.

2. Design: Plan and create a detailed blueprint of how the software will work.

3. Development: Write the actual code based on the design.
4. Testing: Check if the software works correctly and doesn't have any bugs.

5. Deployment: Make the software available to users in a specific environment.

6. Maintenance: Continuously monitor and improve the software even after it's deployed.
