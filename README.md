## Continuous Integration and Continuous Delivery (CI/CD) Pipelines:

Basic Problem State:

For example I have developed an app, and I want to send it to the Quality Assuarance (QA) person to test the app. 

Now one approach is to;

1) Build the apk --release and send it to him on wetransfer.com.

Now here the issue is if I am making changes more than 10 times in a day, so that means I have to send him apk more than 10 timems seperately with each change, which is a very long process.

Now here comes GitHub actions and CI/CD Pipelines.

Now go to your GitHub repository, there must be a button in the tab bar called 'Actions' 

## GitHub Actions:

GitHub Actions is a Continuous Integration and Continuous Delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

For example you are an NodeJS developer, and you want to test the API on the server, then the problem is, you have to individually upload the code on server each time manually (which is a difficult job), there u have to use GitHub actions (CI/CD) pipelines, and your code you automate it, and whenever u push ur code to the GitHub, then the actions on GitHub, the workflow that u have defined on GitHub actions, then it automatically deploys/pushes your code to the server based on your workflow.

In your VS Code flutter project, create a folder '.github' and inside create a folder called 'workflows', then inside make a folder called 'main.yml' 

structure will be like:

.github
	/ workflows
		/ main.yml

For window use this under job  > build > name : runs-on: windows-latest


GitHub actions is a CI/CD platform


Every workflow consists of several different core concepts. These include:

● Events: Events are defined triggers that kick off a workflow. They can be configured to look for one or more triggers and qualified as needed by a developer. They can also be set to run on specific coding branches within a given repository on GitHub.
(It triggers whether we have pushed the code or pulled, etc.)

● Jobs: Jobs are a set of steps that execute on the same runner. Each runs in its own VM and parallel to other jobs, unless otherwise specified.
(Specifies whether we are on mac or windows platform, from where we are pushing it, and it also mentions the steps as well, it mentions architecture as well and also java version and all that it should use, it also mentions that we have to create a release build).

● Steps: Steps are individual tasks that run commands in a job. These can be an action or a shell command. All steps in a job execute on the same runner.

● Actions: An action is a command that’s executed on a runner and the core element of GitHub Actions, which is named after it.

● Runners: A runner is a GitHub Actions server. It listens for available jobs, runs each in parallel, and reports back progress, logs and results. Each runner can be hosted by GitHub or self-hosted on a localized server. GitHub Hosted runners are based on Ubuntu Linux, Windows, and macOS


secrets.TOKEN

Now you have to generate a TOKEN and add it in your GitHub repository. 

GitHub Repository -> Settings -> Secrets and variables -> Actions -> Repository Secrets -> New Repository Secrets 

now write a name of token for example 'TOKEN' this name and that name in secrets.TOKEN should both be same.

Name: TOKEN
Secret: 

for this go to your profile settings.

Profile Settings -> Developer Setytings -> Personal Access Tokens -> Token (classic) -> Generate new token -> new classic token -> select expiry date e.g. 7 days -> Note: GitHub Actions -> Select repo -> Generate Token (green button) -> then copy it and paste it in Secrets -> Add Secrets. 

Now push this code of main.yml 

open commit in vs code then 

create release build -> commit and push -> push 

now go to your github repository -> Actions -> now u can see the comment of create release build (actions) -> click on it and you will see Build & Release -> now when all the processses will be completed -> then you will see it on your GitHub repo.
