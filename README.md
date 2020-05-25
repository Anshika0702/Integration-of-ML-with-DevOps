# Integration-of-ML-with-DevOps
For automated ML model train

*HOW TO INTEGRATE MACHINE LEARNING WITH DEVOPS

->PROBLEM OVERVIEW:
1>Create docker container image that has python installed in it along with all the essential libraries required for training ML model.

2>Create no.of jobs in jenkins to test,notify,rebuild,tweak the MLmodel in order to get desired accuracy.

->SOLUTION OVERVIEW:
We are going to build chain of jobs in order to get desired accuracy for my dataset & for this first we have to create a Dockerfile which will create image with required configurations.
 #JOB 1: It will keep an eye on github repository as soon as developer push something there this job will automatically copy everything in folder of my base OS.
 
 #JOB 2: On success of JOB 1 it will  trigger job to this job will launch docker container which is workspace for Jenkins.
 
 #JOB 3: After successfully launching the OS Jenkins will trigger this job.This job will search for file which is pushed by developer & has a main code to train model.
 
 #JOB 4: It will notify developer that your main code file has some errors due to which job 3 failed.
 
 #JOB 5: If your main file run successfully but give less accuracy than what developer desire then in this case Jenkins should automatically tweak something & also try to increase the accuracy. In order to achieve this things developer will push one more file along with main file. This will help Jenkins to take test and build model again & again till desired accuracy is achieved.
 
 #JOB 6: It will be a success notifier as soon as Jenkins succeed in achieving desired accuracy it will notify developer about success of the model and accuracy achieved.
 
 #JOB 7: It will again failure notifier but now it will notify on failure of your second main file.
 
 #JOB 8: It will be monitoring job.It's job will be to keep an eye on running container. If it found container crashed it will immediately launch new container with same configurations.
