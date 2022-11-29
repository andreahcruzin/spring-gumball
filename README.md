# spring-gumball ci/cd using GCP & GitHub Actions

### This example demonstrates the following two GitHub Workflows.

* https://help.github.com/actions/language-and-framework-guides/building-and-testing-java-with-gradle

* https://github.com/google-github-actions/setup-gcloud/tree/master/example-workflows/gke

### Build Dependencies

* Gradle 5.6
* JDK 11


### Steps to get the application run at GCP
#### 1) Local Running
At the first step it is important to make sure that we are able to run the application in our localhost.
In order to achieve this I imported the application to the Intellij IDE and configured the required JDK and Gradle compiler versions.
Below is the image for the running local version using the IDE.

![SourceCode at Intellij IDE at Localhost](https://github.com/andreahcruzin/LabFiles-Images/blob/main/02.png)

and here is the application:
![Running the App at Localhost](https://github.com/andreahcruzin/LabFiles-Images/blob/main/02.png)


#### 2) GitHub Repo
Then in the 2nd step it is required to create a repository for the source code at my GitHub account. It is better to have locally configured Git for the account since committing via the website is somehow difficult and bothersome.  
Based on the below image it is created and committed successfully. In fact, using this we are able to have latest and all the versions of our application.

![Repo in the profile](https://github.com/andreahcruzin/LabFiles-Images/blob/main/01.png)

and files are as below:

![Repo files](https://github.com/andreahcruzin/LabFiles-Images/blob/main/03.png)


#### 3) GitHub Actions to build code
In this step we are in search of a way to automate this building of our source code which is orchestrated by the Gradle. In fact, all the required steps when we are compiling codes locally to generate and package class files is done via Gradle which is currently managed by the facility of GitHub actions.
In order to achieve this we create the directories in the path and added the "gradle.yml" file which consist all the steps to be done.
Below is the image for this:

![Gradle.yml file creation](https://github.com/andreahcruzin/LabFiles-Images/blob/main/04.png)

After saving and check we got this result:

![GitHub actions result](https://github.com/andreahcruzin/LabFiles-Images/blob/main/05.png)

In order to check everything is working correctly when we are updating the source code. We edited the source code and wait for the result in the actions section of the GitHub repo. Below is the result:

![GitHub repo updated](https://github.com/andreahcruzin/LabFiles-Images/blob/main/06.png)

Below is the result of this update.

![GitHub repo updated and built successfully](https://github.com/andreahcruzin/LabFiles-Images/blob/main/07.png)


#### 4) GitHub Actions to pipeline code to GCP
In this step, we are trying to pipeline the built code to a Google Kubernetes cluster. In fact, we need to configure the credentials for to enable GitHub actions to upload files into the cluster.
Then, to set the steps to do this. 

Below is the image for creating all the secret keys which are taken from the cloud.

![GCP secrets in the GitHub](https://github.com/andreahcruzin/LabFiles-Images/blob/main/12.png)

Also, after setting these keys we added "google.yml" consisting jobs to pipeline built application into the specified GKE.

![google.yml file committed at GitHub repo](https://github.com/andreahcruzin/LabFiles-Images/blob/main/08.png)

This yml file is included in the repo.
After a couple of attempts we could build and deploy our application to the GKE. Below is the image:

![google.yml file committed at GitHub repo](https://github.com/andreahcruzin/LabFiles-Images/blob/main/10.png)


#### 5) Finally
Finally, we waited a little and see the happenings in the cloud. Our app is deployed in the cloud space and we only need to set Ingress to enable outsiders reach the website via proxy.

Below is the result of our application running at GKE using the address: 34.110.147.41

![Application running at GKE](https://github.com/andreahcruzin/LabFiles-Images/blob/main/11.png)
