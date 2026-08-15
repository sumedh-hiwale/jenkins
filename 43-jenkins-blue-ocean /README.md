# 🚀 Jenkins Pipeline as Code Using Blue Ocean Visual Editor

## 📖 Overview

This demo shows how to create a Jenkins Pipeline using the Blue Ocean Visual Editor and automatically generate a Jenkinsfile in a GitHub repository without manually writing pipeline code.

---

## 🎯 Objective

- Create a Pipeline using Blue Ocean UI
- Connect Jenkins with GitHub
- Generate Jenkinsfile automatically
- Execute Build, Test, Parallel and Deploy stages
- Store Pipeline as Code in GitHub

---

## 🛠️ Prerequisites

- Jenkins Installed
- Blue Ocean Plugin Installed
- GitHub Account
- GitHub Repository

---

## 📝 Demo Steps

### 1️⃣ Create GitHub Repository

Created a new GitHub repository:

```text
jenkins-blue-ocean
```

Selected:

- ✅ Add README.md
- ✅ Create Repository

---

### 2️⃣ Install Blue Ocean Plugin

Navigate to:

```text
Manage Jenkins
→ Plugins
→ Available Plugins
→ Search "Blue Ocean"
→ Install
```

---

### 3️⃣ Open Blue Ocean

Navigate to:

```text
Dashboard
→ More Options
→ Open Blue Ocean
```

---

### 4️⃣ Create New Pipeline

Click:

```text
New Pipeline
```

Select:

```text
Where do you store your code?
→ GitHub
```

---

### 5️⃣ Connect GitHub

Click:

```text
Create an access token here
```

GitHub opens automatically.

Provide:

```text
Note: unnati-token
```

Click:

```text
Generate Token
```

Copy the generated token and paste it into:

```text
Connect to GitHub
```

Click:

```text
Connect
```

---

### 6️⃣ Select Repository

Choose repository:

```text
jenkins-blue-ocean
```

Click:

```text
Create Pipeline
```

---

### 7️⃣ Add Build Stage

➕ Add Stage

Stage Name:

```text
Build
```

Add Step:

```text
Shell Script
```

Commands:

```bash
pwd
date
```

---

### 8️⃣ Add Test Stage

➕ Add Stage

Stage Name:

```text
Test
```

Add Step:

```text
Print Message
```

Message:

```text
test step
```

---

### 9️⃣ Add Parallel Stage

Inside Test Stage:

➕ Add Parallel Stage

Stage Name:

```text
Test Par
```

Message:

```text
Test par
```

---

### 🔟 Add Deploy Stage

➕ Add Stage

Stage Name:

```text
Deploy
```

Message:

```text
deploy
```

---

### 1️⃣1️⃣ Add Sleep Step

Inside Deploy Stage:

```text
Add Step → Sleep
```

Time:

```text
13 Seconds
```

---

### 1️⃣2️⃣ Save and Run Pipeline

Click:

```text
Save
```

Description:

```text
Jenkins file added
```

Select:

```text
Commit to Main
```

Click:

```text
Save & Run
```

---

### 1️⃣3️⃣ Verify GitHub Repository

Refresh the repository.

Observe that a new file named:

```text
Jenkinsfile
```

has been automatically created and committed by Blue Ocean.

---

## 📄 Generated Jenkinsfile

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''pwd
date'''
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'testtest step'
          }
        }

        stage('Test Par') {
          steps {
            echo 'Test par'
          }
        }
      }
    }

    stage('Deploy') {
      steps {
        echo 'deploy'
        sleep 13
      }
    }
  }
}
```

---

## ✅ Expected Output

- Blue Ocean Pipeline created successfully
- Jenkinsfile generated automatically
- Jenkinsfile committed to GitHub repository
- Build stage executed successfully
- Parallel stages executed successfully
- Deploy stage executed successfully
- Sleep step executed for 13 seconds

---

## 🔍 Verification

### Jenkins

✅ Blue Ocean Pipeline completed successfully

### GitHub

✅ Jenkinsfile present in repository

### Console Output

```text
pwd
date
testtest step
Test par
deploy
```

---

## 📚 Learning Outcome

- 🎨 Blue Ocean Visual Editor
- 📝 Jenkins Pipeline as Code
- 🔗 GitHub Integration
- ⚙️ Automatic Jenkinsfile Generation
- 🔀 Parallel Stage Execution
- ⏳ Sleep Step Usage
- 📂 Jenkinsfile Version Control
- 🚀 CI/CD Pipeline Creation
- 🎯 Visual Pipeline Design Without Writing Jenkinsfile Manually

---

## 🏆 Conclusion

Successfully created a Jenkins Pipeline using the Blue Ocean Visual Editor, generated a Jenkinsfile automatically, executed multiple stages including parallel execution, and stored the pipeline code in a GitHub repository as part of a Pipeline as Code workflow.
