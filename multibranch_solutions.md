question 1 :

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


question 2

error :
Root cause :
Fix :
Verify :

question 3
question 4
question 5
question 6
