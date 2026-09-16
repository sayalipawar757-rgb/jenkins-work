__question 1__

error : 1. No jenkinsfile found at the expected path.
        2. Skipping build.
        
Root cause : 1. (i) It recognizes the dev branch but not the jenkins file this means ;
                (ii) The jenkinsfile path in the git and while creating a Multibranch pipeline the path and the repository link should be correct.
                (iii) if there is a name conflict means (upper case / Lower case ) or your created the file in another repo/file but in jenkins your giving a wronng path.
             
             2. (i) If it couldn't find jenkinsfile then how it can run a pipeline.
                (ii) Because it failed to find a jenkinsfile in the given path, it will skip the stage called "build".

fix : 1. correct the path in the  multibranch job and check whether its in the correct structure in the git also.
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
error:
Root cause :
Fix :
Verify :

__question 4__
error:
Root cause :
Fix :
Verify :
__question 5__
error:
Root cause :
Fix :
Verify :

