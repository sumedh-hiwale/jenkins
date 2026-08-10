# 🚀 Jenkins Retry Count Demo Using Naginator Plugin

## 🎯 Objective

Demonstrate how Jenkins automatically retries a failed build using the **Naginator Plugin**.

---

## 🛠 Prerequisites

- Jenkins Installed
- Git Plugin Installed
- Naginator Plugin Installed
- GitHub Repository Access

---

## 📝 Steps

### 1️⃣ Install Naginator Plugin

1. Go to **Manage Jenkins** → **Plugins**.
2. Search for **Naginator Plugin**.
3. Install the plugin.
4. Restart Jenkins if required.

---

### 2️⃣ Create a Freestyle Job

1. Click **New Item**.
2. Enter Job Name:

```text
demo-retry
```

3. Select **Freestyle Project**.
4. Click **OK**.

---

### 3️⃣ Configure Git Repository

1. Go to **Source Code Management**.
2. Select **Git**.
3. Enter an invalid repository URL:

```text
https://github.com/SUMEDH-93/demo-jenkins-111
```

4. Leave **Credentials** as **None**.

---

### 4️⃣ Configure Retry Count

1. Scroll to **Post-build Actions**.
2. Click **Add post-build action**.
3. Select **Retry build after failure**.
4. Set:

```text
Maximum number of successive failed builds = 3
```

5. Leave other options as default.

---

### 5️⃣ Save and Build

1. Click **Save**.
2. Click **Build Now**.
3. Open **Build History**.
4. Open **Console Output**.

---

## 📋 Expected Output

```text
Started by user admin
Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'
Finished: FAILURE

Started by Naginator after build #X failure
Fetching changes from the remote Git repository
ERROR: Error fetching remote repo 'origin'
Finished: FAILURE
```

---

## 🔍 Verification

✅ Naginator Plugin is installed.

✅ Build fails due to an invalid Git repository URL.

✅ Jenkins automatically retries the failed build.

✅ Console Output contains:

```text
Started by Naginator after build #X failure
```

✅ Multiple retry builds are created automatically.

✅ Retries stop after reaching the configured limit.

✅ Final Build Status = **FAILURE**.

---

## 🔄 Workflow

```text
Build Started
      ↓
Git Fetch Failed
      ↓
Build FAILURE
      ↓
Naginator Retry #1
      ↓
Build FAILURE
      ↓
Naginator Retry #2
      ↓
Build FAILURE
      ↓
Naginator Retry #3
      ↓
Build FAILURE
      ↓
Retry Limit Reached
```

---

## 🎉 Result

Successfully demonstrated **Retry Count** functionality in Jenkins using the **Naginator Plugin**, where failed builds were automatically retried until the configured retry limit was reached.
