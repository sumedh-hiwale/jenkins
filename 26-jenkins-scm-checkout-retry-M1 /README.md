# 🚀🔄 Jenkins SCM Checkout Retry Count Demo

## 🎯 Objective

Demonstrate how Jenkins automatically retries the SCM (Git Checkout) operation when a Git repository checkout fails.

---

## 📖 What is SCM Checkout Retry Count?

The **SCM Checkout Retry Count** option allows Jenkins to retry Git checkout/fetch operations when temporary failures occur during source code retrieval.

This feature is useful for handling:

* Network connectivity issues
* Temporary Git server unavailability
* Repository access timeouts
* Transient SCM checkout failures

Unlike the **Naginator Plugin**, SCM Checkout Retry Count retries only the Git checkout process and does not rerun the entire build.

---

## 🛠 Prerequisites

* Jenkins Installed
* Git Installed
* Git Plugin Installed

---

## 📝 Steps

### 1️⃣ Create a Freestyle Job

1. Click **New Item**.
2. Enter Job Name:

```text
demo-retry
```

3. Select **Freestyle Project**.
4. Click **OK**.

---

### 2️⃣ Configure Git Repository

1. Go to **Source Code Management**.
2. Select **Git**.
3. Enter an invalid repository URL:

```text
https://github.com/SUMEDH-93/demo-jenkins-111
```

4. Leave **Credentials** as **None**.

---

### 3️⃣ Configure SCM Checkout Retry Count

1. Go to **General**.
2. Click **Advanced**.
3. Enable **Retry Count**.
4. Set:

```text
SCM checkout retry count = 3
```

---

### 4️⃣ Save and Build

1. Click **Save**.
2. Click **Build Now**.
3. Open **Console Output**.

---

## 📋 Expected Output

```text
Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'

Retrying SCM checkout...

Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'

Retrying SCM checkout...

Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'

Retrying SCM checkout...

Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'

Finished: FAILURE
```

---

## 🔍 Verification

✅ Retry Count option is enabled.

✅ SCM checkout retry count is set to 3.

✅ Jenkins retries Git checkout automatically.

✅ No new build numbers are created.

✅ Retries occur within the same build.

✅ Final Build Status = FAILURE.

---

## 🔄 Workflow

```text
Build Start
     ↓
Git Checkout
     ↓
Checkout Failed
     ↓
Retry Checkout #1
     ↓
Checkout Failed
     ↓
Retry Checkout #2
     ↓
Checkout Failed
     ↓
Retry Checkout #3
     ↓
Checkout Failed
     ↓
Build FAILURE
```

---

## 📌 Difference from Naginator Plugin

| SCM Checkout Retry Count      | Naginator Plugin             |
| ----------------------------- | ---------------------------- |
| Retries Git Checkout Only     | Retries Entire Build         |
| Same Build Execution          | Creates New Build Executions |
| No Additional Plugin Required | Requires Naginator Plugin    |
| Used for SCM Failures         | Used for Build Failures      |

---

## 🎉 Result

Successfully demonstrated the **SCM Checkout Retry Count** feature in Jenkins. When the Git checkout operation failed, Jenkins automatically retried the SCM checkout process three times before marking the build as failed.
A
