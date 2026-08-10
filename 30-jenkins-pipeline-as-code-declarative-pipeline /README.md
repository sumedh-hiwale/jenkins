# 🚀 Create First Pipeline as Code (Jenkinsfile)

## 🎯 Objective

Create and execute a Jenkins Pipeline using a Jenkinsfile (Pipeline Script) and verify stage execution through Console Output and Stage View.

---

## 📋 Prerequisites

* Jenkins Installed and Running
* Access to Jenkins Dashboard
* Jenkins Agent/Node Connected
* User with Job Creation Permissions

---

## 🛠️ Step 1: Create a New Pipeline Job

1. Login to **Jenkins Dashboard**
2. Click **New Item**
3. Enter Job Name:

```text
Pipeline-as-code-Hello-world
```

4. Select **Pipeline**
5. Click **OK**

---

## ⚙️ Step 2: Configure Pipeline Script

1. Scroll down to the **Pipeline** section.
2. Select:

```text
Definition = Pipeline Script
```

3. Click **Try Sample Pipeline**
4. Select **Hello World**

Generated Pipeline Script:

```groovy
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```

5. Click **Save**

---

## ▶️ Step 3: Execute the Pipeline

1. Click **Build Now**
2. Open the build number
3. Click **Console Output**

### Expected Output

```text
Started by user admin
Hello World
Finished: SUCCESS
```

---

## ✏️ Step 4: Modify the Pipeline Script

1. Click **Configure**
2. Replace the existing script with:

```groovy
pipeline {
    agent any

    stages {
        stage('test') {
            steps {
                echo 'test'
            }
        }

        stage('build') {
            steps {
                echo 'build'
            }
        }

        stage('Deploy on test') {
            steps {
                echo 'Deploy on test'
            }
        }

        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod'
            }
        }
    }
}
```

3. Click **Save**

---

## 🔄 Step 5: Rebuild the Pipeline

1. Click **Build Now**
2. Open the latest build
3. Click **Console Output**

### Expected Output

```text
Started by user admin

test
build
Deploy on test
Deploy on prod

Finished: SUCCESS
```

---

## 📊 Step 6: Verify Stage View

1. Open the completed build
2. Click **Stages**

### Expected Stages

```text
test
build
Deploy on test
Deploy on prod
```

All stages should display a ✅ green status.

---

## 🔁 Pipeline Flow

```text
Start
  ↓
test
  ↓
build
  ↓
Deploy on test
  ↓
Deploy on prod
  ↓
End
```

---

## ✅ Verification

* Pipeline Job created successfully
* Jenkinsfile executed successfully
* All stages executed sequentially
* Console Output displayed expected messages
* Build Status shows SUCCESS
* Stage View shows all stages completed successfully

---

## 📸 Output

### Console Output

```text
test
build
Deploy on test
Deploy on prod
Finished: SUCCESS
```

### Stage View

```text
✅ test
✅ build
✅ Deploy on test
✅ Deploy on prod
```

---

## 🎉 Conclusion

Successfully created a Jenkins Pipeline using a Jenkinsfile (Pipeline Script), modified the stages, executed the pipeline, and verified successful execution through Console Output and Jenkins Stage View.

This demonstrates the basic concept of **Pipeline as Code** in Jenkins using a Declarative Pipeline.
