# 🚀 Build after other project are build (jenkins upstream and downstream)

## 🎯 Objective

Configure a Jenkins Downstream Job (`demo-5th`) that automatically triggers after the successful completion of an Upstream Job (`demo-4th`).

---

## 📋 Prerequisites

* Jenkins Installed and Running
* Access to Jenkins Dashboard
* Existing Freestyle Job: `demo-4th`

---

## 🏗️ Workflow

```text
demo-4th
    ↓
Build Success
    ↓
demo-5th
    ↓
echo "Hello World"
    ↓
SUCCESS
```

---

## 🚀 Step 1: Create Downstream Job

* Jenkins Dashboard → New Item
* Enter Job Name: `demo-5th`
* Select **Freestyle Project**
* Click **OK**

---

## 🚀 Step 2: Configure Build Trigger

* Open `demo-5th`
* Click **Configure**
* Navigate to **Build Triggers**
* Select:

```text
Build after other projects are built
```

* In **Projects to watch**, enter:

```text
demo-4th
```

* Select:

```text
Trigger only if build is stable
```

---

## 🚀 Step 3: Add Build Step

* Scroll to **Build Steps**
* Click **Add Build Step**
* Select **Execute Shell**

Enter:

```bash
echo "Hello World"
```

---

## 🚀 Step 4: Save Configuration

* Click **Save**

---

## 🚀 Step 5: Trigger Upstream Job

* Open `demo-4th`
* Click **Build Now**

---

## ✅ Verification

### Verify Upstream Build

* Open `demo-4th`
* Confirm Build Status is **SUCCESS**

### Verify Downstream Build

* Open `demo-5th`
* Verify a new build starts automatically

### Verify Console Output

`demo-5th` → Build Number → Console Output

```text
Started by upstream project "demo-4th"

+ echo "Hello World"
Hello World

Finished: SUCCESS
```

---

## 🎉 Result

Successfully configured Jenkins Upstream and Downstream Jobs where:

* `demo-4th` acts as the Upstream Job
* `demo-5th` acts as the Downstream Job
* `demo-5th` is triggered automatically after a successful build of `demo-4th`
* The Downstream Job executes the shell command and prints:

```text
Hello World
```
