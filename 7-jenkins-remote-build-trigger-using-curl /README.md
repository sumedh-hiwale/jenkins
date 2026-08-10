# 🚀 Jenkins Remote Build Trigger Using cURL and Authentication Token

## 🎯 Steps

### 1️⃣ Install Plugin

* Manage Jenkins → Plugins
* Search **Build Authorization Token Root**
* Install Plugin

### 2️⃣ Configure Job

* Open Job **demo-test1**
* Click **Configure**
* Enable **Trigger builds remotely (e.g., from scripts)**

### 3️⃣ Configure Token

Enter Authentication Token:

```text
mytoken123
```

### 4️⃣ Configure Execute Shell

Add the following command:

```bash
echo "Hello World"
```

### 5️⃣ Save Job

Click **Save** 💾

### 6️⃣ Reference URL Format

```text
buildByToken/build?job=RevolutionTest&token=TacoTuesday
```

### 7️⃣ Replace Job Name and Token

```text
JENKINS_URL/job/test1/build?token=mytoken123 
```

### 8️⃣ Trigger Build from Terminal

```bash

curl http://100.31.79.29:8080/buildByToken/build?job=test1\&token=mytoken123
```

### 9️⃣ Verify Build

* Open Jenkins Dashboard
* Open Job **demo-test1**
* Check **Build History**
* Verify a new build is created

### 🔟 Check Console Output

Expected Output:

```text
Hello World
```

### 1️⃣1️⃣ Confirm Success

✅ Build Triggered Successfully

✅ Token Authentication Working

✅ cURL Request Executed Successfully

✅ Jenkins Job Completed Successfully

---

## 🔄 Workflow

```text
💻 Terminal
      ↓
📡 cURL Request
      ↓
🔐 Token Authentication
      ↓
⚙️ Jenkins Receives Request
      ↓
🚀 demo-test1 Job Triggered
      ↓
🖥️ Execute Shell Runs
      ↓
💬 Hello World Printed
      ↓
✅ Build Successful
```

## 🎉 Result

The Jenkins job **demo-test1** was successfully triggered remotely using **cURL** and an **Authentication Token**.
