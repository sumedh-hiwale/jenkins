# 🚀 Jenkins Pipeline as Code with GitHub

## 📌 Objective

Demonstrate how Jenkins fetches a **Jenkinsfile** from a GitHub repository and executes the pipeline using **Pipeline Script from SCM**.

---

## 🛠️ Prerequisites

* Jenkins Server Running
* GitHub Account
* Git Plugin Installed in Jenkins
* Access to a GitHub Repository

---

## 📂 GitHub Repository

**Repository Name:**

```text
jenkins-pipeline-as-code
```

**File Name:**

```text
Jenkinsfile
```

---

## 📝 Demo Steps

### 1️⃣ Create a GitHub Repository

Create a GitHub repository named:

```text
jenkins-pipeline-as-code
```

### 2️⃣ Create a Jenkinsfile

Create a file named:

```text
Jenkinsfile
```

### 3️⃣ Add Pipeline Code

Paste the pipeline code into the Jenkinsfile and commit the changes to GitHub.

### 4️⃣ Create a New Pipeline Job

Open Jenkins Dashboard.

Click:

```text
New Item
```

### 5️⃣ Enter Job Details

Job Name:

```text
pipeline-as-code-from-github
```

Select:

```text
Pipeline
```

Click **OK**.

### 6️⃣ Configure Pipeline from SCM

Open **Configure**.

Scroll to the **Pipeline** section.

Configure:

```text
Definition = Pipeline script from SCM

SCM = Git

Repository URL =
https://github.com/sumedh-hiwale/jenkins-pipeline-as-code.git

Branch Specifier =
*/main

Script Path =
Jenkinsfile
```

### 7️⃣ Save Configuration

Click **Save**.

### 8️⃣ Trigger Build

Click:

```text
Build Now
```

### 9️⃣ View Console Output

Open the latest build.

Click:

```text
Console Output
```

Verify the pipeline execution.

---

## ✅ Expected Output

* Jenkins connects to GitHub.
* Jenkins clones the repository.
* Jenkins fetches the Jenkinsfile from GitHub.
* Pipeline stages execute successfully.
* Input approval step appears.
* Remaining stages execute after approval.
* Post actions run successfully.

---

## 🔍 Verification

Verify the Console Output contains entries similar to:

```text
Obtained Jenkinsfile from git
```

```text
Checking out Revision
```

```text
Cloning the remote Git repository
```

```text
Running on Jenkins
```

Also verify:

✅ Environment Variables are displayed

✅ Parameters are available

✅ Input approval step appears

✅ Pipeline completes successfully

---

## 🎉 Result

Successfully demonstrated **Jenkins Pipeline as Code with GitHub**, where Jenkins retrieves the Jenkinsfile from a GitHub repository using SCM and executes the pipeline automatically.
