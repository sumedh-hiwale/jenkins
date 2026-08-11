# 🚀 Parallel Job in Jenkins Build Pipeline

## 🎯 Objective

Demonstrate Parallel Job Execution in Jenkins Build Pipeline where multiple downstream jobs run simultaneously after the successful completion of an upstream job.

---

## 🛠 Prerequisites

- Jenkins Installed
- Build Pipeline Plugin Installed
- Existing Jobs:
  - project1-build
  - project1-test-deploy
  - project1-prod-deploy
- Build Pipeline View Created (`project1-view`)

---

## 📝 Steps

### 1️⃣ Create Code Quality Job

- Click **New Item**
- Enter Job Name:

```text
project1-CQ
```

- Select **Freestyle Project**
- Click **OK**

---

### 2️⃣ Configure Code Quality Job

Go to:

**Build → Execute Shell**

Add the following commands:

```bash
echo "Code Quality Check"
sleep 10
```

- Click **Save**

---

### 3️⃣ Configure Upstream Job

Open:

```text
project1-build
```

Click:

**Configure**

Go to:

**Post-build Actions**

Select:

**Build other projects**

Enter:

```text
project1-test-deploy,project1-CQ
```

- Click **Save**

---

### 4️⃣ Verify Build Pipeline View

Open:

```text
project1-view
```

Verify that both jobs appear at the same level:

```text
project1-build

      ├── project1-test-deploy
      └── project1-CQ

               ↓

      project1-prod-deploy
```

---

### 5️⃣ Run the Pipeline

- Open **project1-view**
- Click **Run**

Execution Flow:

```text
project1-build
        ↓
project1-test-deploy
        &
project1-CQ
```

Both jobs start simultaneously after the successful completion of `project1-build`.

---

### 6️⃣ Observe Production Deployment

After completion of:

```text
project1-test-deploy
project1-CQ
```

Observe that:

```text
project1-prod-deploy
```

does not start automatically because it is configured as a manual deployment stage.

---

## 📊 Pipeline Flow

```text
project1-build
        ↓
 ┌───────────────┬───────────────┐
 ↓               ↓
project1-test-deploy    project1-CQ
        │
        ▼
project1-prod-deploy (Manual)
```

---

## ✅ Expected Output

- `project1-build` runs successfully.
- `project1-test-deploy` starts automatically.
- `project1-CQ` starts automatically.
- Both downstream jobs run in parallel.
- `project1-prod-deploy` remains in manual state.

---

## 🔍 Verification

✔ Verify `project1-build` executes successfully.

✔ Verify `project1-test-deploy` and `project1-CQ` start simultaneously.

✔ Verify both jobs appear at the same level in Build Pipeline View.

✔ Verify parallel execution is visible in Jenkins.

✔ Verify `project1-prod-deploy` does not start automatically.

✔ Verify production deployment requires manual execution.

---

## 🎉 Conclusion

Successfully demonstrated **Parallel Job Execution in Jenkins Build Pipeline** where `project1-test-deploy` and `project1-CQ` ran simultaneously after the successful completion of `project1-build`, while `project1-prod-deploy` remained a manual deployment stage.
