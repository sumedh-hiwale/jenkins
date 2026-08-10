# 🚀 Jenkins Poll SCM Integration

## 📌 Objective

To configure Jenkins Poll SCM and automatically trigger builds whenever changes are detected in a GitHub repository.

---

## 🛠️ Prerequisites

* Jenkins Installed and Running
* Git Plugin Installed
* GitHub Account
* Internet Connectivity

---

## 📋 Steps Performed

### Step 1: Create a Freestyle Project

1. Open Jenkins Dashboard.
2. Click **New Item**.
3. Enter the project name as **demo-poll-build**.
4. Select **Freestyle Project**.
5. Click **OK**.

---

### Step 2: Configure Poll SCM

1. Navigate to the **Build Triggers** section.
2. Enable **Poll SCM**.
3. Enter the following schedule:

```bash
*/1 * * * *
```

4. This schedule instructs Jenkins to check the Git repository every 1 minute.

---

### Step 3: Create a GitHub Repository

1. Create a new GitHub repository named:

```text
demo-jenkins
```

---

### Step 4: Create README.md File

Add the following content to the README.md file:

```md
# demo-jenkins - test1
```

Commit and save the file.

---

### Step 5: Create index.html File

Create an index.html file with the following content:

```html
<html>
<body>
    <h1> this is sumedh hiwale </h1>
</body>
</html>
```

Commit and save the file.

---

### Step 6: Configure Git Repository in Jenkins

1. Copy the HTTPS URL of the GitHub repository.
2. Open the **demo-poll-build** project in Jenkins.
3. Click **Configure**.
4. Navigate to **Source Code Management**.
5. Select **Git**.
6. Paste the repository URL into **Repository URL**.

---

### Step 7: Configure Branch

In the **Branches to build** section, enter:

```text
*/main
```

---

### Step 8: Save the Job

Click **Save** to save the Jenkins job configuration.

---

### Step 9: Verify Initial Build

1. Wait for approximately 1 minute.
2. Jenkins checks the Git repository.
3. The first build is automatically triggered.

---

### Step 10: Verify No Build Without Changes

1. Wait for several more minutes.
2. No new build is triggered.
3. Jenkins does not trigger a build because no new commit is detected.

---

### Step 11: Modify README.md File

Edit the README.md file.

**Before**

```md
# demo-jenkins - test1
```

**After**

```md
# demo-jenkins - test2
```

Commit and save the changes.

---

### Step 12: Verify Automatic Build Trigger

1. Return to Jenkins.
2. Wait approximately 1 minute.
3. Jenkins checks the repository again.
4. Jenkins detects the new commit.
5. A new build is automatically triggered.

---

## ✅ Verification

* Poll SCM successfully checked the repository every 1 minute.
* No build was triggered when there were no repository changes.
* After modifying the README.md file, Jenkins detected the new commit.
* Jenkins automatically triggered a new build.
* This confirms that Poll SCM triggers builds only when changes are detected in the configured Git repository.

---

## 🎯 Conclusion

Successfully configured Jenkins Poll SCM with a GitHub repository. Jenkins continuously monitored the repository and automatically triggered a new build whenever a new commit was detected.
