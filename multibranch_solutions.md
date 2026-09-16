__question 1__

error : 1. No jenkinsfile found at the expected path.
        2. Skipping build.
        
Root cause : 
             1. (i) It recognizes the dev branch but not the jenkins file this means ;
                (ii) The jenkinsfile path in the git and while creating a Multibranch pipeline the path and the repository link                      should be correct.
                (iii) if there is a name conflict means (upper case / Lower case ) or your created the file in another repo/                          file but in jenkins your giving a wronng path.
             
             2. (i) If it couldn't find jenkinsfile then how it can run a pipeline.
                (ii) Because it failed to find a jenkinsfile in the given path, it will skip the stage called "build".

fix :
      1. correct the path in the  multibranch job and check whether its in the correct structure in the git also.
      2. if the path is fixed and it finds jenkisfile the it'll run the whole pipeline and also stage "build".

verify : scan the multibranch job and check the console output to see if its actually succeeded or  failed.


__question 2__

error :  The condition/format in the pipeline is invalid " branchName  ' main ' " in the when block{}

Root cause : The branchname is not a valid syntax/format to match a branch 

Fix : I replaced the branchName condition with just only branch in when block{}

Verify : Console Output

Started by user sayali pawar
Seen branch in repository origin/main
Obtained Jenkinsfile from 22670688a8bbcaf67c72e89b0b64e74ab2c6e22d
[Pipeline] Start of Pipeline
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ echo Running tests
Running tests
[Pipeline] }
[Pipeline] End of Pipeline
Finished: SUCCESS

__question 3__

error: feature/payment exists in Git but does not appear in Jenkins.

Root cause :  In Jenkins Multibranch Pipeline has not discovered/indexed the new branch, or discover branch is not enabled.

Fix :  (a) jenkins-side :
             (i) Check Jenkins Job configuration page  
             (ii) enable discover branch if its not selected
             (iii)  save it and click on  Scan Multibranch Pipeline Now. 
       (b) Git-side : 
               verify with  :
                     (i) git brannch : shows current root branch.
                     (ii) git remote -v : checks git connection to the repo.
                     (iii) git status : to check if there is any changes.
Verify : Check the Jenkins indexing log and confirm feature/payment appears as a new branch job.

__question 4__
cause 1 : Wrong revision/branch  selected in checkout configuration

Error : Jenkins says it is building feature/payment, but the checked-out commit belongs to the release branch.

Root Cause : The SCM/checkout configuration may be using a fixed revision, wrong branch specifier, 
              or an incorrect environment variable instead of dynamically checking out feature/payment.

Fix : Correct the SCM configuration to explicitly use the feature/payment branch/ref and    
      ensure the checkout step uses that branch's revision. Remove any hard-coded release revision.
Verify : Run the build again and check the console for Checking out revision. Confirm that the commit 
        hash matches the current feature/payment head and that the commit message is from the payment feature branch.

cause 2 : Repository state in a Multibranch workspace

Error : The job is building feature/payment, but an old release checkout remains in the workspace.
Root Cause : A Multibranch Pipeline may be reusing a workspace from another branch/job, or the previous checkout 
             was not cleaned correctly. This can leave the workspace at an old release revision.
Fix : Clean/delete the existing workspace and perform a fresh SCM checkout. Configure branch-specific workspaces or ensure the        pipeline performs a clean checkout before building.

Verify : Re-run the feature/payment build after cleaning the workspace. Check git branch, git rev-parse HEAD, and the console            checkout message to confirm that the workspace contains the expected feature/payment.

Overall verification  : Confirm that the checked-out commit hash is da?456 (the expected feature/payment commit) and that the                           console no longer shows the “Merge main into release” commit.

__question 5__
error:  The Deploy condition is allowing branches other than main to reach the Deploy stage.

Root cause : The when condition is not restricted properly to the main branch.

Fix : Change the Deploy condition so that it allows deployment only from the `main` branch. This will prevent dev and feature/         branches from deploying.

Verify : I would run the pipeline on all three branches and check the Jenkins console. Deploy should run only for main.

Jenkins successfully checked the GitHub repository and found the Jenkinsfile on the main branch. No new changes were detected, so the branch indexing completed successfully.

Result: Finished: SUCCESS



