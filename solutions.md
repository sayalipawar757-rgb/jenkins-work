Question 1 : 
Trigger option: Poll SCM
Why webhooks won't work: The Jenkins server has no public IP/publicly reachable endpoint, so GitHub cannot send a webhook request to Jenkins.
Therefore, 
Jenkins must periodically check the GitHub repository for changes.
Polling schedule (cron): H/5 * * * *
This checks the repository approximately every 5 minutes and triggers a build when a change is detected.

Question 2 : 
The pipeline has four stages: Checkout, Build, Test and Deploy. The Deploy stage uses the when block so it runs only on the main branch. 
The post { always } block archives the test reports even if a stage fails.
The success and failure blocks print different messages depending on the build result.

Question 3 :
1. Stages block is missing : stages {} is missing inside the pipeline. It should be there to keep all the stages.
2. Stages is written inside Checkout : There is a stages {} inside  Checkout . This is wrong. A stage should have  steps  inside it.
3. Unit Tests is missing{} : stage('Unit Tests') does not have braces. We need {} after the stage name.
4. Pipeline closing bracket is missing : The pipeline {} is not closed before the post {} block starts.
5. Closing brackets are missing at the end : The always {} and post {} blocks are not closed properly. Some }are missing.
6. Build and Parallel Tests are in Checkout :  Because of the wrong stages {}placement, Build and Parallel Tests are coming inside Checkout. They should be separate stages.

Question 4 :
I changed the given Jenkins code into a Declarative Pipeline. I used pipeline and agent any to tell Jenkins where to run the code. 
I added the environment variable APP_ENV as staging. I kept retry(3) so Jenkins will try the build three times if it does not work. 
For the testing part, I used `catchError` so that even if the test fails, Jenkins will mark the build as UNSTABLE instead of stopping completely. 
Declarative Pipeline is a good choice because the code is simple, organized, and easy to understand.

Question 5 :
1. Workspace already locked
The most likely cause is that two builds of nightly-build are running at the same time and trying to use the same workspace.
Fix: Disable concurrent builds in the Jenkins job configuration so only one build can use the workspace at a time.

2. Permission denied while writing build.log
The Jenkins user does not have sufficient write permission for the workspace or build.log. This can happen if the files are owned by another user.
Fix: Change the workspace/file ownership and permissions so the Jenkins agent user has permission to read and write the workspace.

3. Stale copy of the repository
Jenkins is reusing an old workspace/repository instead of getting a completely fresh copy, so the latest commit may not be checked out.
Fix: In the Git SCM configuration, enable “Wipe out repository and force clone” (or “Clean before checkout”) 
so Jenkins cleans the old repository before checking out the latest code.
