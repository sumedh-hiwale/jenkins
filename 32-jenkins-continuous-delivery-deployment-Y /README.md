# 🚀 Jenkins Continuous Deployment & Continuous Delivery Demo Using Build Pipeline Plugin

## 🎯 Objective

Demonstrate the difference between Continuous Deployment and Continuous Delivery using Jenkins Build Pipeline Plugin.

---

# 🔄 Continuous Deployment Demo

In Continuous Deployment, the Production Deployment job starts automatically after the Test Deployment job completes successfully.

## 🛠 Steps

### 1️⃣ Create Production Deployment Job

- Click **New Item**
- Enter Job Name:

```text
project1-prod-deploy
```

- Select **Freestyle Project**
- Click **OK**

---

### 2️⃣ Configure Production Deployment Job

Go to:

```text
project1-prod-deploy → Configure
```

Under **Build → Execute Shell**, add:

```bash
sleep 10
echo "deploying to production enviroment"
```

Click **Save**

---

### 3️⃣ Configure Automatic Deployment

Go to:

```text
project1-test-deploy → Configure
```

Click:

```text
Add post-build action
```

Select:

```text
Build other projects
```

Configure:

```text
Projects to build:
project1-prod-deploy

☑ Trigger only if build is stable
```

Click **Save**

---

### 4️⃣ Open Build Pipeline View

Click the **+** icon and open:

```text
Project1-view
```

Pipeline will appear as:

```text
project1-test-deploy
          ↓
project1-prod-deploy
```

---

### 5️⃣ Run Pipeline

Run:

```text
project1-test-deploy
```

---

### 6️⃣ Verify Automatic Deployment

After successful completion of:

```text
project1-test-deploy
```

Jenkins automatically triggers:

```text
project1-prod-deploy
```

without any manual intervention.

---

## ✅ Expected Output

```text
project1-test-deploy completed successfully.
project1-prod-deploy started automatically.
Finished: SUCCESS
```

---

## 🔍 Verification

- No manual trigger required.
- Production deployment starts automatically after successful Test Deployment.

---

# 📦 Continuous Delivery Demo

In Continuous Delivery, the Production Deployment job waits for manual approval/trigger after the Test Deployment job completes successfully.

## 🛠 Steps

### 1️⃣ Open Test Deployment Job Configuration

Go to:

```text
project1-test-deploy → Configure
```

---

### 2️⃣ Remove Automatic Deployment Trigger

Under **Post-build Actions**, remove:

```text
Build other projects
```

which was previously configured as:

```text
project1-prod-deploy
```

---

### 3️⃣ Configure Manual Deployment Step

Click:

```text
Add post-build action
```

Select:

```text
Build other projects (manual step)
```

Configure:

```text
Downstream Project Names:
project1-prod-deploy
```

Click **Save**

---

### 4️⃣ Open Build Pipeline View

Click the **+** icon and open:

```text
Project1-view
```

Pipeline remains visible.

---

### 5️⃣ Run Test Deployment Job

Run:

```text
project1-test-deploy
```

Wait for successful completion.

---

### 6️⃣ Manually Trigger Production Deployment

After Test Deployment succeeds:

Click the small **▶ Run** button beside:

```text
project1-prod-deploy
```

This manually starts the Production Deployment job.

---

### 7️⃣ Verify Console Output

Open:

```text
project1-prod-deploy → Console Output
```

Verify:

```bash
sleep 10
deploying to production enviroment
Finished: SUCCESS
```

---

## ✅ Expected Output

```text
project1-test-deploy completed successfully.
project1-prod-deploy did not start automatically.
project1-prod-deploy started only after manual trigger.
Finished: SUCCESS
```

---

## 🔍 Verification

- Manual approval/trigger required before Production Deployment.
- Production Deployment starts only when the user clicks **Run**.
- Continuous Delivery workflow achieved successfully.

---

# 🎉 Conclusion

### 🚀 Continuous Deployment

```text
Build
  ↓
Test
  ↓
Production Deployment (Automatic)
```

✅ No manual intervention required.

---

### 📦 Continuous Delivery

```text
Build
  ↓
Test
  ↓
Manual Approval
  ↓
Production Deployment
```

✅ Deployment is ready but requires manual trigger before release.

---

## 💡 Key Difference

| Continuous Deployment | Continuous Delivery |
|----------------------|--------------------|
| Automatic Production Deployment | Manual Production Deployment |
| No Human Intervention | Human Approval Required |
| Faster Releases | More Controlled Releases |
