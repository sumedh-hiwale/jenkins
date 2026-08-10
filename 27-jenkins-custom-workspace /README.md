# 🚀 Jenkins Custom Workspace Demo

## 🎯 Objective

Demonstrate how to change the default Jenkins workspace location using the **Custom Workspace** option.

---

## 🛠️ Prerequisites

* Jenkins Installed
* Freestyle Project Created
* Access to Jenkins Server Terminal

---

## 📝 Steps

### 1️⃣ Create a Freestyle Job

Create a new Freestyle Project.

**Job Name**

```text
demo-custom-workspace
```

---

### 2️⃣ Configure Build Step

Go to:

```text
Configure → Build Steps → Execute Shell
```

Add the following command:

```bash
pwd
touch abc.txt
ls
pwd
```

Click **Save**.

---

### 3️⃣ Run Build Using Default Workspace

Click **Build Now**.

Open **Console Output** and verify the default workspace location:

```text
/var/lib/jenkins/workspace/demo-custom-workspace
```

Example Output:

```text
+ pwd
/var/lib/jenkins/workspace/demo-custom-workspace
+ touch abc.txt
+ ls
abc.txt
+ pwd
/var/lib/jenkins/workspace/demo-custom-workspace
Finished: SUCCESS
```

---

### 4️⃣ Configure Custom Workspace

Go to:

```text
Configure → General → Advanced
```

Enable:

```text
Use Custom Workspace
```

Enter the custom workspace path:

```text
/tmp/mytest
```

Click **Save**.

---

### 5️⃣ Verify Directory Before Build

Login to the Jenkins Server and check the `/tmp` directory:

```bash
cd /tmp
ls
```

Verify that the `mytest` directory does not exist before running the build.

---

### 6️⃣ Run Build Again

Click **Build Now**.

Open **Console Output**.

Verify that Jenkins is now using the custom workspace:

```text
Building in workspace /tmp/mytest
```

---

### 7️⃣ Verify on Jenkins Server

Login to the Jenkins Server and run:

```bash
cd /tmp/mytest
ls
```

Verify that the file has been created:

```text
abc.txt
```

---

## ✅ Expected Output

```text
Started by user admin
Running as SYSTEM
Building in workspace /tmp/mytest

[mytest] $ /bin/sh -xe /tmp/jenkins15182959447325770068.sh

+ pwd
/tmp/mytest

+ touch abc.txt

+ ls
abc.txt

+ pwd
/tmp/mytest

Finished: SUCCESS
```

---

## 🔍 Verification

### Default Workspace

```text
/var/lib/jenkins/workspace/demo-custom-workspace
```

### Custom Workspace

```text
/tmp/mytest
```

### Verify File Creation

```bash
cd /tmp/mytest
ls
```

Output:

```text
abc.txt
```

---

## 🎉 Result

✅ Jenkins successfully changed the workspace location from:

```text
/var/lib/jenkins/workspace/demo-custom-workspace
```

to

```text
/tmp/mytest
```

✅ Jenkins automatically created the custom workspace directory during the build.

✅ The file `abc.txt` was created inside the custom workspace.

✅ The build completed successfully using the new workspace location.
