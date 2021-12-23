# Demo of Deploying Dotnet web application  using Git action to Azure

  ### 1) Create dotnet web application 
  Running below command creates an dot net web applicaiton which we will use to demo actions
  

>`dotnet new webapp -f netcoreapp3.1 -o DotnetDemoapp`

>`cd DotnetDemoapp/`


![Create webapp](/images/Step1CreateProject.png)


### 2) Initialize git repository and add the files to the repository
Execute the command in below order

a) Initialize git repo
>$ `git init`

![Initialize repo](/images/Step2-GitInit.png)

b)Link the local file to the git remote repository
>$ `git remote add origin git@github.com:miltonfdo/ActionsDemo.git`

![Link to remote repo](/images/Step3LinkToRemote.png)


c) Add all files to local staging
>$`git add .`

>$`git commit -m "add base application"`

![Add to Local](/images/Step4AddToLocal.png)
![Commit to staging](/images/Step4aCommitToLocal.png)

d) Push the files to remote repository(GIT)
>$`git push -u origin master`

![Push to git](/images/Step5PushToOrgin.png)


### 3) Create action workflows

Actions can be invoked based on multiple events 

![Actions, based on events](/images/GITActionsFlow.png)


To start with ,in the root folder of the application create folder with below structure *".github/workflows"*

a) Git action workflow are defined using YAML file,Create an yam file *"build.yml"* under the workflow folder

![Actions, based on events](/images/ActionsFolderStructure.png)


### 4) Update YAML file with the steps

Since in the demo application we have choosen in an dotnet we will follow the below steps

1) Dotnet restore - which get all depencies of the project

2) Dotnet build - which builds the applicaiton

3) Dotnet publish - which is used to publish all production 
files to a folder

4) move the published file to Azure - we use Azure publish profile with secrets to perform this operation

5) keep a copy of artificat in github - A copy of the publish folder/artifact is pushed to github for any troubleshooting or future reference
  
![Actions, based on events](/images/Step6ActionConfig.png)

### 5)Commit back the Yaml file
Commit the changes made to the YAML file back to GIT

a) Add files to local
>`git add .`

b) commit the changes

>`git commit -m "adding ci to git"`

c) Push to staging
>`git push`

![Step7CommitYAML](/images/Step7CommitYAML.png)

### 6) Workflow execution:

Once the changes are pushed ,it would be effective including the commit which pushed the actions to repo.

![Step8WorkFlowExecuted](/images/Step8WorkFlowExecuted.png)

The steps we have mentioned in the logs can be seen build logs with details on each operation performed

![Step8aBuildDetails](/images/Step8aBuildDetails.png)


Build logs with steps
![Step8bBuildSubDetails](/images/Step8bBuildSubDetails.png)


### 7) Checking at Azure and the deployed application


Azure configuration
![Step9AzureView](/images/Step9AzureView.png)


### 8) Deployed web application

Application is deployed here - https://az-lunuxgithubdemo.azurewebsites.net



![Step10WebApp](/images/Step10WebApp.png)
