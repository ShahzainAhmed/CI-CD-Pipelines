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

### Key Components of a GitHub Actions Workflow

- ### Events 
    Events are triggers that start a workflow. They can be configured to respond to one or more triggers and can be restricted to specific branches within a repository. Examples include pushing code, creating a pull request, or other repository activities.

- ### Jobs
    Jobs are sets of steps that execute on the same runner. Each job runs in its own virtual machine and runs in parallel with other jobs unless specified otherwise. Jobs define the platform (e.g., macOS, Windows), architecture, Java version, and other environment settings. They also include the steps required, such as building a release.

- ### Steps 
    Steps are individual tasks within a job. Each step can run a shell command or use an action. All steps in a job execute sequentially on the same runner.

- ### Actions
    An action is a reusable command or script executed on a runner. Actions are the core building blocks of GitHub Actions workflows and can be shared across workflows.

- ### Runners: 
    A runner is a server that executes jobs. It listens for available jobs, runs them, and reports progress, logs, and results. Runners can be hosted by GitHub (GitHub-hosted runners) or self-hosted on a local server. GitHub-hosted runners support Ubuntu Linux, Windows, and macOS.

`secrets.TOKEN`

You need to generate a TOKEN and add it to your GitHub repository:

1. Go to your GitHub repository.

2. Navigate to Settings → Secrets and variables → Actions → Repository secrets.

3. Click New repository secret and add your TOKEN there.

When creating your secret, make sure the name of the token matches what you use in your workflow `secrets.TOKEN`.
```
Name: TOKEN
Secret: [Paste your generated token here]
```
This ensures that in your workflow file, when you reference secrets.TOKEN, GitHub knows which secret to use.

### Generating a Personal Access Token for GitHub Actions

Profile Settings -> Developer Settings -> Personal Access Tokens -> Token (classic) -> Generate new token -> new classic token -> select expiry date e.g. 7 days -> Note: GitHub Actions -> Select repo -> Generate Token (green button) -> then copy it and paste it in Secrets -> Add Secrets. 

1. Go to your GitHub profile settings.
2. Navigate to Developer settings → Personal access tokens → Tokens (classic).
3. Click Generate new token → New classic token.
4. Set an expiry date (e.g., 7 days).
5. Add a Note, e.g., GitHub Actions.
6. Select the repository the token should have access to.
7. Click Generate token (green button).
8. Copy the token and paste it in your repository:
   - Go to Settings → Secrets and variables → Actions → Repository secrets → New repository secret.
   - Add a Name (e.g., TOKEN) and paste your token in the Secret field.
   - Click Add secret.
     
Now push this code of main.yml 

### Push your `main.yml` Code and Trigger the Workflow

1. Open your Flutter project in VS Code.
2. Open the **Source Control / Commit** panel.
3. Ensure your `main.yml` file is added in `.github/workflows`.
4. Create a release build of your app.
5. Commit your changes and push them to GitHub.
6. Go to your **GitHub repository → Actions** tab.
7. Find the workflow run labeled **“Create Release Build”**.
8. Click on the workflow to view the **Build & Release** progress.
9. Once the workflow completes successfully, your build/release will be available in your GitHub repository.

