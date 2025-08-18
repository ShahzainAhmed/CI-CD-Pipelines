## Continuous Integration and Continuous Delivery (CI/CD) Pipelines:

### Basic Problem State:

For example, I have developed an app and I want to send it to the Quality Assurance (QA) team for testing.

One common approach is to:

Build the release APK and send it to them via a file-sharing service like WeTransfer.

However, the issue arises if I make more than 10 changes in a single day. This would mean I need to build and send the APK separately more than 10 times, which is time-consuming.

This is where GitHub Actions and CI/CD pipelines come in.

Now, go to your GitHub repository. In the top tab bar, you will see a button called "Actions".

## GitHub Actions

GitHub Actions is a Continuous Integration and Continuous Delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

For example, if you are a NodeJS developer and want to test the API on the server, the problem is that you need to manually upload the code to the server each time, which is a difficult task. To solve this, you can use GitHub Actions (CI/CD pipelines) to automate the process. Whenever you push your code to GitHub, the workflow you defined in GitHub Actions will automatically deploy or push your code to the server.

In your VS Code Flutter project, create a folder named `.github`, then inside it create another folder named `workflows`. Inside the workflows folder, create a file called `main.yml`.

### Folder Structure
```
.github
    └── workflows
        └── main.yml
```
For Windows, use the following under `job > build`:
```
name: build
runs-on: windows-latest
```

### Every workflow in GitHub Actions consists of several core concepts

### Events 
Events are triggers that start a workflow. They can be configured to respond to one or more triggers and can be restricted to specific branches within a repository. Examples include pushing code, creating a pull request, or other repository activities.

### Jobs
Jobs are sets of steps that execute on the same runner. Each job runs in its own virtual machine and runs in parallel with other jobs unless specified otherwise. Jobs define the platform (e.g., macOS, Windows), architecture, Java version, and other environment settings. They also include the steps required, such as building a release.

### Steps 
Steps are individual tasks within a job. Each step can run a shell command or use an action. All steps in a job execute sequentially on the same runner.

### Actions
An action is a reusable command or script executed on a runner. Actions are the core building blocks of GitHub Actions workflows and can be shared across workflows.

### Runners: 
A runner is a server that executes jobs. It listens for available jobs, runs them, and reports progress, logs, and results. Runners can be hosted by GitHub (GitHub-hosted runners) or self-hosted on a local server. GitHub-hosted runners support Ubuntu Linux, Windows, and macOS.

`secrets.TOKEN`

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
