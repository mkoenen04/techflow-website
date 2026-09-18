# Workflow Analysis

## 1. What triggers this workflow to run?
Push and pull requests.

## 2. What are the four main steps this workflow performs?
Step 1: Get the code from the repository
Step 2: Validate HTML files  
Step 3: Check for broken links
Step 4: Upload the built site for deployment

## 3. What does the "Checkout code" step do and why is it necessary?
It uses the actions/checkout@v4 action to copy the repo's files onto the GitHub actions runner. It's necessary because each workflow run starts on a fresh, empty virtual machine. It has no access to your code by default, so without this step, none of the later steps would have any files to work with.

## 4. What is the purpose of the environment configuration?
It links the deploy job to the GitHub pages environment which is used to track deployments and can apply rules. The url line also grabs the live site link once it's deployed so it shows up on the workflow run page.

## 5. How does this automated deployment improve reliability compared to manual deployment?
If I was deploying manually I could forget a step or skip checking for broken code or links before pushing something. This way it's the same steps every single time, and it won't even deploy if the validation steps fail, so broken stuff doesn't make it to the actual site.

## 6. What would happen if you pushed code to a different branch (not main)?
Nothing would happen because the on: section only looks for pushes made in the main branch.