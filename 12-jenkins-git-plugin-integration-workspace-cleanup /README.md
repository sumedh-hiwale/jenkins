# demo-jenkins - test1

---

# 🚀 Jenkins Git Plugin Integration and Workspace Cleanup

## 🎯 Objective

Understand the difference between Manual Git Clone and Jenkins Git Plugin checkout. Also understand how the "Delete workspace before build starts" option works in Jenkins.

---

## 📋 Prerequisites

- Jenkins Installed
- Git Installed
- GitHub Account
- Public GitHub Repository

---

# Part 1: Manual Git Clone Using Execute Shell

## Step 1: Create GitHub Repository

Repository Name:

```text
demo-jenkins
```

Create the following files:

### README.md

```text
# demo-jenkins
```

### index.html

```html
<html>
<body>
    <h1> this is sumedh hiwale </h1>
</body>
</html>
```

Commit and Push the files to GitHub.

---

## Step 2: Create Jenkins Freestyle Job

Create a new Freestyle Project:

```text
demo-3rd
```

---

## Step 3: Add Build Step

Navigate to:

```text
Build Steps → Execute Shell
```

Add the following commands:

```bash
echo "Hello World"
ls
git clone https://github.com/SUMEDH-93/demo-jenkins.git
cd demo-jenkins
ls
cat index.html
cat README.md
```

Save the job.

---

## Step 4: Build the Job

Click:

```text
Build Now
```

### Expected Result

Repository gets cloned successfully.

Workspace:

```text
workspace/
└── demo-jenkins/
    ├── README.md
    └── index.html
```

Build Status:

```text
SUCCESS
```

---

## Step 5: Run Build Again

Click:

```text
Build Now
```

again.

### Error Observed

```bash
fatal: destination path 'demo-jenkins' already exists and is not an empty directory.
```

### Reason

The repository folder already exists from the previous build.

Workspace:

```text
workspace/
└── demo-jenkins/
```

When Jenkins runs:

```bash
git clone https://github.com/SUMEDH-93/demo-jenkins.git
```

Git fails because the destination directory already exists.

Build Status:

```text
FAILED
```

---

## Step 6: Enable Workspace Cleanup

Navigate to:

```text
Configure
    ↓
Environment
    ↓
Delete workspace before build starts
```

Enable the option and save the job.

---

## Step 7: Build Again

Click:

```text
Build Now
```

### Result

Before build starts Jenkins automatically deletes the workspace.

```text
workspace/
```

becomes empty.

Then:

```bash
git clone https://github.com/SUMEDH-93/demo-jenkins.git
```

runs successfully.

Workspace:

```text
workspace/
└── demo-jenkins/
    ├── README.md
    └── index.html
```

Build Status:

```text
SUCCESS
```

---

## Observation

### Without Workspace Cleanup

```text
Build Start
      ↓
Old Repository Exists
      ↓
git clone Fails
      ↓
Build Failed
```

### With Workspace Cleanup

```text
Build Start
      ↓
Delete Workspace
      ↓
git clone
      ↓
Build Success
```

---

# Part 2: Using Jenkins Git Plugin

## Step 1: Create New Freestyle Job

Create a Freestyle Project:

```text
demo-4th
```

---

## Step 2: Configure Git Repository

Navigate to:

```text
Source Code Management
    ↓
Git
```

Repository URL:

```text
https://github.com/SUMEDH-93/demo-jenkins.git
```

Credentials:

```text
None
```

Save the configuration.

---

## Step 3: Add Build Step

Navigate to:

```text
Build Steps
    ↓
Execute Shell
```

Add:

```bash
ls
cat README.md
cat index.html
```

Save the job.

---

## Step 4: Run Build

Click:

```text
Build Now
```

### What Jenkins Does Internally

```text
GitHub Repository
        ↓
Jenkins Git Plugin
        ↓
git fetch
git checkout
        ↓
Workspace Updated
        ↓
Execute Shell Runs
```

### Output

```bash
README.md
index.html
```

```html
<html>
<body>
    <h1> this is sumedh hiwale </h1>
</body>
</html>
```

Build Status:

```text
SUCCESS
```

---

## Step 5: Modify GitHub Repository

Open:

```text
README.md
```

Change content to:

```text
# demo-jenkins - test1
```

Commit the changes.

Commit Message:

```text
Update project title in README.md
```

---

## Step 6: Run Jenkins Job Again

Click:

```text
Build Now
```

### Console Output

```bash
Fetching changes from the remote Git repository

Checking out Revision 3e54466afbb7a28aa557347827ceb2775b5b21ae

Commit message:
"Update project title in README.md"

+ ls
README.md
index.html

+ cat README.md
# demo-jenkins - test1

+ cat index.html
<html>
<body>
    <h1> this is sumedh hiwale </h1>
</body>
</html>

Finished: SUCCESS
```

### Observation

Jenkins automatically fetched the latest commit from GitHub.

No manual Git commands were required.

---

# Workflow Comparison

## Manual Git Clone

```text
Jenkins
   ↓
Execute Shell
   ↓
git clone
   ↓
Repository Downloaded
```

## Jenkins Git Plugin

```text
GitHub Repository
        ↓
Jenkins Git Plugin
        ↓
git fetch
git checkout
        ↓
Workspace Updated
        ↓
Build Step Executed
```

---

# Conclusion

- Manual `git clone` works but can fail if the repository already exists.
- `Delete workspace before build starts` removes old files before every build.
- Jenkins Git Plugin automatically fetches and checks out the latest code.
- Jenkins Git Plugin is the recommended approach for CI/CD pipelines.
- Any changes pushed to GitHub are automatically fetched during the next build.
- Using **Source Code Management → Git** is better than manually running `git clone` in Execute Shell.

---
