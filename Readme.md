DevOps Automation Project:-
We had to create two environments - the production environment and testing environment. Under this we have 3 jobs - the production job,
the developer job and the test_merge job that wouls completely automate the task of running a webpage as 
well as updating it after any changes made in the production environment.
I have created a simple github repository containing a basic html file (url) , followed by the github branche - master branch and dev1 branch. 
Deployment of the jobs given are as follows:-

#Job1 : If Developer pushes to dev1 branch then Jenkins will fetch from dev1 and deploy on dev-docker environment. 
I created a job named devjob and devos . When the developer commits any further code, it is automatically pushed to github using a post-commit github hook.
When this is successful, the next job chained with it, that is devjob is initiated along with the initiation of docker environment, which is done by devos.

#Job2 : If Developer push to master branch then Jenkins will fetch from master and deploy on master-docke environment.
Both dev-docker and master-docker environment are on different docker containers.
I have created a job named devjob2 which will copy and paste the github repository into a folder and also launch a docker environment from which 
clients can connect.

#Job3 : Jenkins will check (test) for the website running in dev-docker environment. If it is running fine then Jenkins will merge the dev branch to 
master branch and trigger #job2
This is actually a testing environment. The QA team will manually test the deployment of job1 and if it is running successfully then job2 will be 
triggerred as well as the origin/master branch will be merged with full automation.

In order to make my webpage accessible to the public even with a private ip, I have used ngrok tunnelling using which i converted my private ip to public 
ip.