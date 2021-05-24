# Deploy-to-Kubernetes-in-Google-Cloud



Deploy to Kubernetes in Google Cloud: Challenge Lab
1 hour 30 minutes
9 Credits
Rate Lab
GSP318

Google Cloud Self-Paced Labs

Overview
In a challenge lab you’re given a scenario and a set of tasks. Instead of following step-by-step instructions, you will use the skills learned from the labs in the quest to figure out how to complete the tasks on your own! An automated scoring system (shown on this page) will provide feedback on whether you have completed your tasks correctly.

When you take a challenge lab, you will not be taught new Google Cloud concepts. You are expected to extend your learned skills, like changing default values and reading and researching error messages to fix your own mistakes.

To score 100% you must successfully complete all tasks within the time period!

This lab is recommended for studetns who have enrolled in the Deploy to Kubernetes in Google Cloud quest. Are you ready for the challenge?

Topics tested:

Creating Docker images on a host.
Running Docker containers on a host.
Storing Docker images in the Google Container Repository (GCR).
Deploying GCR images on Kubernetes.
Pushing updates onto Kubernetes.
Automating deployments to Kubernetes using Jenkins.
Setup
Before you click the Start Lab button
Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Google Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access Google Cloud for the duration of the lab.

What you need
To complete this lab, you need:

Access to a standard internet browser (Chrome browser recommended).
Time to complete the lab.
Note: If you already have your own personal Google Cloud account or project, do not use it for this lab.

Note: If you are using a Pixelbook, open an Incognito window to run this lab.

How to start your lab and sign in to the Google Cloud Console
Click the Start Lab button. If you need to pay for the lab, a pop-up opens for you to select your payment method. On the left is a panel populated with the temporary credentials that you must use for this lab.

Open Google Console

Copy the username, and then click Open Google Console. The lab spins up resources, and then opens another tab that shows the Sign in page.

Sign in

Tip: Open the tabs in separate windows, side-by-side.

If you see the Choose an account page, click Use Another Account. Choose an account
In the Sign in page, paste the username that you copied from the Connection Details panel. Then copy and paste the password.

Important: You must use the credentials from the Connection Details panel. Do not use your Qwiklabs credentials. If you have your own Google Cloud account, do not use it for this lab (avoids incurring charges).

Click through the subsequent pages:

Accept the terms and conditions.
Do not add recovery options or two-factor authentication (because this is a temporary account).
Do not sign up for free trials.
After a few moments, the Cloud Console opens in this tab.

Note: You can view the menu with a list of Google Cloud Products and Services by clicking the Navigation menu at the top-left. Cloud Console Menu
Challenge scenario
You have just completed training on containers and their creation and management and now you need to demonstrate to the Jooli Inc. development team your new skills. You have to help with some of their initial work on a new project around an application environment utilizing Kubernetes. Some of the work was already done for you, but other parts require your expert skills.

You are expected to create container images, store the images in a repository, and configure a Jenkins CI/CD pipeline to automate the build for the product. Your know that Kurt, your supervisor, will ask you to complete these tasks:

Create a Docker image and store the Dockerfile.
Test the created Docker image.
Push the Docker image into the Container Repository.
Use the image to create and expose a deployment in Kubernetes
Update the image and push a change to the deployment.
Create a pipeline in Jenkins to deploy a new version of your image when the source code changes.
Some Jooli Inc. standards you should follow:

Create all resources in the us-east1 region and us-east1-b zone, unless otherwise directed.

Use the project VPCs.

Naming is normally team-resource, e.g. an instance could be named kraken-webserver1.

Allocate cost effective resource sizes. Projects are monitored and excessive resource use will result in the containing project's termination (and possibly yours), so beware. This is the guidance the monitoring team is willing to share: unless directed, use n1-standard-1.

Your challenge
As soon as you sit down at your desk and open your new laptop you receive the following request to complete these tasks. Good luck!

Do not wait for the lab to provision! You can work through tasks 1-3 before you need the provisioning to be finished. Just ensure the workstation exists before starting Task 1.
Task 1: Create a Docker image and store the Dockerfile
Open Cloud Shell and run source <(gsutil cat gs://cloud-training/gsp318/marking/setup_marking.sh). This command will install marking scripts you can use to help check your progress.

Use Cloud Shell to clone the valkyrie-app source code repository (it is in your project).

The app source code is in valkyrie-app/source. Create valkyrie-app/Dockerfile and add the configuration below.

FROM golang:1.10
WORKDIR /go/src/app
COPY source .
RUN go install -v
ENTRYPOINT ["app","-single=true","-port=8080"]
Use valkyrie-app/Dockerfile to create a Docker image called valkyrie-app with the tag v0.0.1

Once you have created the Docker image, and before clicking Check my progress, run step1.sh to perform the local check of your work. After you get a successful response from the local marking you can check your progress.

Click Check my progress to verify the objective.
Create a Docker image and store the Dockerfile

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 2: Test the created Docker image
Launch a container using the image valkyrie-app:v0.0.1. You need to map the host’s port 8080 to port 8080 on the container. Add & to the end of the command to cause the container to run in the background.

When your container is running you will see the page by Web Preview.

Once you have your container running, and before clicking Check my progress, run step2.sh to perform the local check of your work. After you get a successful response from the local marking you can check your progress.

Click Check my progress to verify the objective.
Test the created Docker image

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 3: Push the Docker image in the Container Repository
Push the Docker image valkyrie-app:v0.0.1 into the Container Registry.

Make sure you re-tag the container to gcr.io/YOUR_PROJECT/valkyrie-app:v0.0.1.

Click Check my progress to verify the objective.
Push the Docker image in the Google Container Repository

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 4: Create and expose a deployment in Kubernetes
Kurt created the deployment.yaml and service.yaml to deploy your new container image to a Kubernetes cluster (called valkyrie-dev). The two files are in valkyrie-app/k8s.

Remember you need to get the Kubernetes credentials before you deploy the image onto the Kubernetes cluster.

Before you create the deployments make sure you check the deployment.yaml and service.yaml files. Kurt thinks they need some values set (he thinks he left some placeholder values).

You can check the load balancer once it’s available.

Click Check my progress to verify the objective.
Create and expose a deployment in Kubernetes

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 5: Update the deployment with a new version of valkyrie-app
Before deploying the new code, increase the replicas from 1 to 3 to ensure you don't cause an outage.

Click Check my progress to verify the objective.
Increase the replicas from 1 to 3

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Kurt made changes to the source code (he put the changes in a branch called kurt-dev). You need to merge kurt-dev into master (you should use git merge origin/kurt-dev).

Build the new code as version v0.0.2 of valkyrie-app, push the updated image to the Container Repository, and then redeploy to the valkyrie-dev cluster. You will know you have the new v0.0.2 version because the titles for the cards will be green.

Click Check my progress to verify the objective.
Update the deployment with a new version of valkyrie-app

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 6: Create a pipeline in Jenkins to deploy your app
This process of building the container and pushing to the container repository can be automated using Jenkins. There is a Jenkins deployment in your valkyrie-dev cluster - connect to Jenkins and configure a job to build when you push a change to the source code.

Remember with Jenkins:

Get the password with printf $(kubectl get secret cd-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo.

Connect to the Jenkins console using the commands below (but make sure you don't have a running container docker ps; if you do, kill it):

export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/component=jenkins-master" -l "app.kubernetes.io/instance=cd" -o jsonpath="{.items[0].metadata.name}")
kubectl port-forward $POD_NAME 8080:8080 >> /dev/null &
Setup your credentials to use Google Service Account from metadata.
Create a pipeline job that points to your */master branch on your source code.
Make two changes to your files before you commit and build:

Edit valkyrie-app/Jenkinsfile and change YOUR_PROJECT to your actual project id.
Edit valkyrie-app/source/html.go and change the two occurrences of green to orange.
Use git to:

Add all the changes then commit those changes to the master branch.
Push the changes back to the repository.
When you are ready, manually trigger a build (the initial build will take some time, so just monitor the process). The build will replace the running containers with containers with different tags; you will see orange colored headings.

Click Check my progress to verify the objective.
Create a pipeline in Jenkins to deploy your app

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.

Congratulations!
You did!
