<h1>DevOps-Task2</h1>
<h2>Objective :-</h2>
<h3>To Integrate Docker with Jenkins.</h3>

<h3>Steps :-</h3>

1. Create container image that’s has Jenkins installed using dockerfile. 

2. When we launch this image, it should automatically starts Jenkins service in the container.

3. Create a job chain of job1, job2, job3 and job4 using build pipeline plugin in Jenkins. 

4.  Job 1 : Pull  the Github repo automatically when some developers push repo to Github.

5.  Job 2 : By looking at the code or program file, Jenkins should automatically start the respective language interpreter (eg. If code is of  PHP, then Jenkins should start the container that has PHP already installed ).

6. Job 3 : Test your app if it  is working or not.

7. Job 4 : if app is not working , then send email to developer with error messages.

8. Create One extra job job5 for monitor : If container where app is running. fails due to any reson then this job should automatically start the container again.

<h3>Requirements :-</h3>
 
 1. Knowledge of Docker.
 
 2. Knowledge of Jenkins.
 
 <h3>Solution :-</h3>
 
 First of all, I have created a Dockerfile having jenkins configured.
 
 ![1](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/dockerfile.png)
 
 After this we build it using the command <b> docker build -t jenkins:v1  .<b>
 
 Here, jenkins is the image name, v1 is the version name and '.' refers to the location where Dockerfile is located.
 
 Now to run it use the command :-
 
 ![2](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/dockersock.png)
 
 After running it we'll get the jenkins password, using which we'll unlock jenkins by going to the specified ip and port number.
 
 ![3](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/unlockjen.png)

 On logging in we'll download plugins like git, github and build pipelines to set-up our jenkins server.
 
 Once we have set-up the server we'll start creating our jobs.
 
 <h3>JOB 1 :-</h3>
 
 ![4](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/job1.png)
 ![5](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/job1.1.png)
 
 Job 1 will pull the Github repo automatically when some developers push repo to Github.
 
 <h3>JOB 2 :-</h3>
 
 ![6](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/job2.png)
 
 It is the downstream job of Job 1. This job will automatically start the respective language interpreter by looking at the code.
 
 <h3>JOB 3 :-</h3>
 
 ![7](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/job3.png)
 
 It is the downstream job of Job 2. This job is used for testing purpose.
 
 <h3>JOB 4 :-</h3>
 
 This job is used as a downstream for Job 3 which will send the message to the developers about the failure of the app. To send mail to the developers, we'll first have to configure the email-notification settings.
 
 <b>Go to Manage Jenkins → Configure System → Under E-mail Notification apply the following changes with our credentials.
  
 ![8](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/emailconfig.png)
 
 After that configure the build of Job 4 and provide the email address where we want to receive the message.
 
 ![9](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/Job4.png)
 
 <h3>JOB 5 :-</h3>
 
 Job 5 is used for monitoring purpose. If due to any reason the app fails, it will automatically start the container again.
 
 ![11](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/Job5.png)
 
 <h3>Build Pipeline View :-</h3>
 
 ![10](https://github.com/gauravsjc02/DevOps-Task2/blob/master/task2/buildpipe.png)
