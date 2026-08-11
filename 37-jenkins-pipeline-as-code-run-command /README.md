# 🚀 Jenkins Pipeline as Code - Run a Command

## 📌 Objective
Execute Linux shell commands inside a Jenkins Declarative Pipeline and verify the output using Console Output and Stage View.

---

## 🛠️ Prerequisites

- Jenkins Server Running
- Existing Pipeline Job: `Pipeline-as-code-Hello-world`
- Access to Jenkins Dashboard

---

## 📝 Steps

### Step 1: Open Existing Pipeline Job

- Login to Jenkins
- Open **Pipeline-as-code-Hello-world**

---

### Step 2: Update Pipeline Script

- Click **Configure**
- Replace/Update the pipeline script with:

```groovy
pipeline {
    agent any

    stages {
        stage('Run a Command') {
            steps {
                sh 'date'
                sh 'ls'
                sh 'pwd'
            }
        }
        stage('build') {
            steps {
                echo 'build'
            }
        }
        stage('Deploy on test') {
            steps {
                echo 'Deploy on test1'
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

- Click **Save**

---

### Step 3: Execute Pipeline

- Click **Build Now**

---

## 📊 Expected Output

### Console Output

```bash
+ date
Mon Jun 15 18:10:35 UTC 2026

+ ls

+ pwd
/var/lib/jenkins/workspace/Pipeline-as-code-Hello-world

build
Deploy on test1
Deploy on prod1

Finished: SUCCESS
```

### Stage View

```text
✅ Run a Command
✅ build
✅ Deploy on test
✅ Deploy on prod
```

---

## 🔍 Verification

- Verify build status is **SUCCESS**
- Verify `date` command executed successfully
- Verify `pwd` command displays Jenkins workspace path
- Verify all stages completed successfully
- Verify Stage View shows all stages in green

---

## 📚 Commands Used

| Command | Purpose |
|----------|----------|
| `date` | Display current system date and time |
| `ls` | List files and directories in workspace |
| `pwd` | Display current working directory |

---

## 🎯 Result

- Successfully executed Linux shell commands using Jenkins Declarative Pipeline.
- Verified command execution through Console Output.
- Verified successful stage execution through Stage View.
- Pipeline completed successfully with status **SUCCESS**. ✅
