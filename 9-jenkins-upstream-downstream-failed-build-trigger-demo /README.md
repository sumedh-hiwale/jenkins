# 🚀 Build after Other Projects are Built (Unstable Job Jenkins) - Part 2

## 🎯 Objective

Demonstrate how a downstream Jenkins job can be triggered even when the upstream job fails using the **Trigger even if the build fails** option.

---

## 📋 Prerequisites

* Jenkins Installed and Running
* Existing Upstream Job: `demo-4th`
* Existing Downstream Job: `demo-5th`

---

## 🚀 Steps

### 1. Open the `demo-4th` job and click **Configure**.

### 2. Navigate to **Build Steps** → **Execute Shell**.

### 3. Enter an invalid command to simulate a failed build.

### 4. Click **Save**.

### 5. Open the `demo-5th` job and click **Configure**.

### 6. Navigate to **Build Triggers**.

### 7. Configure the following:

```text
Build after other projects are built
Projects to watch: demo-4th
Trigger even if the build fails
```

### 8. Click **Save**.

### 9. Run the `demo-4th` job.

### 10. Verify that `demo-4th` fails.

### 11. Verify that `demo-5th` is triggered automatically despite the upstream build failure.

---

## ✅ Verification

### Verify Upstream Job

* Open `demo-4th`
* Confirm Build Status is **FAILED**

### Verify Downstream Job

* Open `demo-5th`
* Verify that a new build is triggered automatically

### Verify Console Output

`demo-5th` → Build Number → Console Output

```text
Started by upstream project "demo-4th"

Finished: SUCCESS
```

---

## 🔄 Workflow

```text
demo-4th
    ↓
Build Failed
    ↓
Trigger even if the build fails
    ↓
demo-5th
    ↓
Build Triggered
    ↓
SUCCESS
```

---

## 🎉 Result

* `demo-4th` failed due to the invalid command.
* `demo-5th` was triggered automatically even though the upstream job failed.
* This demonstrates the functionality of **Trigger even if the build fails** in Jenkins Upstream and Downstream Jobs.
