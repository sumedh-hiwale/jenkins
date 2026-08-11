# 🚀 Jenkins Pipeline as Code - Input Parameters & User Approval

## 🎯 Objective

This demo demonstrates:

- 📝 String Parameter
- ☑️ Boolean Parameter
- 📋 Choice Parameter
- 👤 User Input During Build
- ⏸️ Pipeline Pause for Approval
- ✅ Manual Approval Before Production Deployment

---

## 📋 Prerequisites

- Jenkins Server Running
- Existing Pipeline Job: `Pipeline-as-code-Hello-world`

---

## 🛠️ Steps

### 1️⃣ Open Existing Pipeline

- Login to Jenkins.
- Open **Pipeline-as-code-Hello-world**.
- Click **Configure**.

---

### 2️⃣ Add Pipeline Script

- Navigate to the **Pipeline** section.
- Add the following Jenkinsfile:

```groovy
pipeline {
    agent any

    environment {
        name = 'sumedh'
    }

    parameters {
        string(name: 'person', defaultValue: 'unnati development', description: 'Who are you?')
        booleanParam(name: 'isMale', defaultValue: true, description: '')
        choice(name: 'city', choices: ['jaipur', 'mumbai', 'pune'], description: '')
    }

    stages {

        stage('Run a Command') {
            steps {
                sh 'date'
                sh 'ls'
                sh 'pwd'
            }
        }

        stage('Environment Variable') {
            environment {
                username = 'myusername'
            }

            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }

        stage('Parameters') {
            steps {
                echo 'Deploy on test1'
                sh 'echo "${name}"'
                sh 'echo "${person}"'
            }
        }

        stage('Continue ?') {
            input {
                message 'Should We Continue ?'
                ok "Yes We should"
            }

            steps {
                echo 'Deploy on prod1'
            }
        }

        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod1'
            }
        }
    }
}
```

---

### 3️⃣ Save Configuration

- Click **Save**.

---

### 4️⃣ Build With Parameters

- Click **Build with Parameters**.

Jenkins displays the following parameters:

#### 📝 String Parameter

```text
person
Who are you?
unnati development
```

#### ☑️ Boolean Parameter

```text
isMale
True
```

#### 📋 Choice Parameter

```text
city
Jaipur
Mumbai
Pune
```

---

### 5️⃣ Start Build

- Keep default values.
- Click **Build**.

---

### 6️⃣ Verify Initial Pipeline Execution

Pipeline executes the following stages:

#### 🖥️ Run a Command Stage

Commands Executed:

```bash
date
ls
pwd
```

Example Output:

```text
Wed Jun 17 13:37:41 UTC 2026

/var/lib/jenkins/workspace/Pipeline-as-code-Hello-world
```

---

#### 🌍 Environment Variable Stage

Commands Executed:

```bash
echo "${BUILD_ID}"
echo "${name}"
echo "${username}"
```

Output:

```text
21
sumedh
myusername
```

---

#### 📝 Parameters Stage

Commands Executed:

```bash
echo "${name}"
echo "${person}"
```

Output:

```text
sumedh
unnati development
```

---

### 7️⃣ Pipeline Waits for Approval

Pipeline reaches the following stage:

```groovy
stage('Continue ?')
```

Console Output:

```text
Should We Continue ?
Yes We should or Abort
```

⏸️ Pipeline execution pauses and waits for manual approval.

---

### 8️⃣ Approve the Build

- Open the running build.
- Click **Stages**.
- Open **Continue ?** stage.

You will see:

```text
Should We Continue ?

Yes We should
Abort
```

- Click **✅ Yes We should**.

---

### 9️⃣ Verify Approval

Output:

```text
Wait for interactive input

Should We Continue ?
Yes We should or Abort

Approved by admin
```

Jenkins resumes pipeline execution.

---

### 🔟 Verify Production Deployment

Pipeline executes:

```groovy
echo 'Deploy on prod1'
```

Output:

```text
Deploy on prod1
```

---

### 1️⃣1️⃣ Verify Build Status

Build Result:

```text
SUCCESS
```

---

## 🔍 Parameter Types Used

| Parameter | Type | Purpose |
|------------|---------|---------|
| 📝 person | String | Accept user input |
| ☑️ isMale | Boolean | Accept True/False value |
| 📋 city | Choice | Select one option from list |

---

## 🔍 Input Step Used

```groovy
input {
    message 'Should We Continue ?'
    ok "Yes We should"
}
```

### Purpose

- ⏸️ Pause Pipeline Execution
- 👤 Wait for User Approval
- ▶️ Continue Build on Approval
- ❌ Abort Build if Rejected
- 🚀 Commonly Used Before Production Deployment

---

## ✅ Expected Output

- 🖥️ Commands executed successfully
- 🌍 Environment variables printed
- 📝 Parameter values displayed
- ⏸️ Pipeline paused for approval
- ✅ User approved build
- 🚀 Production deployment executed
- 🎉 Build completed successfully

---

## ✔ Verification

- [x] Build with Parameters option visible
- [x] String parameter accepted input
- [x] Boolean parameter displayed
- [x] Choice parameter dropdown displayed
- [x] Pipeline paused for approval
- [x] Manual approval screen appeared
- [x] Build resumed after approval
- [x] Build completed successfully

---

## 🎉 Result

Successfully demonstrated:

✅ Pipeline as Code  
✅ String Parameter  
✅ Boolean Parameter  
✅ Choice Parameter  
✅ User Input During Build  
✅ Manual Approval Process  
✅ Production Deployment Confirmation  
✅ Successful Pipeline Execution 🚀
