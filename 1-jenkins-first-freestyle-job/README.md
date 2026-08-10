# 🚀 Jenkins First Freestyle Job - Hello World

## 🎯 Objective

Create and execute the first Jenkins Freestyle Job to print **Hello World** using the Execute Shell build step.

---

## 📋 Prerequisites

* Jenkins Installed
* Jenkins Dashboard Accessible
* Admin User Login

---

## 🏗️ Workflow

```text
Jenkins Dashboard
        ↓
Create Freestyle Project
        ↓
Add Build Step
        ↓
Execute Shell
        ↓
echo "Hello World"
        ↓
Build Now
        ↓
SUCCESS
```

---

## Step 1: Login to Jenkins

Open Jenkins Dashboard:

```text
http://<EC2-PUBLIC-IP>:8080
```

---

## Step 2: Create a New Freestyle Project

```text
Dashboard
    ↓
New Item
    ↓
Name: demo-first
    ↓
Freestyle Project
    ↓
OK
```

---

## Step 3: Add Build Step

```text
Build Steps
    ↓
Add Build Step
    ↓
Execute Shell
```

Add the following command:

```bash
echo "Hello World"
```

Click **Save**.

---

## Step 4: Run the Job

```text
demo-first
    ↓
Build Now
```

---

## Step 5: View Console Output

```text
Build History
    ↓
#1
    ↓
Console Output
```

Expected Output:

```bash
Started by user admin

+ echo Hello World
Hello World

Finished: SUCCESS
```

---

## ✅ Result

Successfully created and executed the first Jenkins Freestyle Job and printed:

```text
Hello World
```

**Build Status:** ✅ SUCCESS
