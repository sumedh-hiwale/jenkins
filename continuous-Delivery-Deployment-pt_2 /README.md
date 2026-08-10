# 🚀 Continuous Deployment & Continuous Delivery Demo Using Build Pipeline Plugin

## 🎯 Objective

Demonstrate the difference between:

- ✅ Continuous Deployment (Automatic Production Deployment)
- ✅ Continuous Delivery (Manual Production Deployment)

using Jenkins Build Pipeline Plugin.

---

# 🚀 Demo 1: Continuous Deployment

## 🎯 Objective

Demonstrate Continuous Deployment where production deployment happens automatically after successful testing.

---

## 🛠️ Prerequisites

- Jenkins Installed
- Build Pipeline Plugin Installed
- Existing Jobs:
  - `project1-build`
  - `project1-test-deploy`

---

## 📝 Steps

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

Navigate to:

```text
project1-prod-deploy → Configure
```

Add **Execute Shell** build step:

```bash
sleep 10
echo "deploying to production environment"
```

Click **Save**

---

### 3️⃣ Configure Automatic Production Deployment

Navigate to:

```text
project1-test-deploy → Configure
```

Click:

```text
Add Post-build Action
```

Select:

```text
Build other projects
```

Configure:

```text
Projects to build:
project1-prod-deploy
```

Enable:

```text
Trigger only if build is stable
```

Click **Save**

---

### 4️⃣ Open Build Pipeline View

Navigate to:

```text
Project1-view
```

Verify the pipeline:

```text
project1-build
       ↓
project1-test-deploy
       ↓
project1-prod-deploy
```

---

### 5️⃣ Run Pipeline

Click **Run** from Build Pipeline View.

---

## ✅ Expected Output

```text
project1-build         SUCCESS
project1-test-deploy   SUCCESS
project1-prod-deploy   SUCCESS
```

---

## 🔍 Verification

✅ `project1-test-deploy` completes successfully

✅ `project1-prod-deploy` starts automatically

✅ No manual trigger required

✅ Complete pipeline executes automatically

---

## 🎉 Conclusion

```text
Build
  ↓
Test
  ↓
Production Deployment
```

🚀 Production deployment happens automatically after successful testing.

---

# 🚀 Demo 2: Continuous Delivery

## 🎯 Objective

Demonstrate Continuous Delivery where production deployment requires manual approval before deployment.

---

## 🛠️ Prerequisites

- Jenkins Installed
- Build Pipeline Plugin Installed
- Existing Jobs:
  - `project1-build`
  - `project1-test-deploy`
  - `project1-prod-deploy`

---

## 📝 Steps

### 1️⃣ Open Test Deployment Job

Navigate to:

```text
project1-test-deploy → Configure
```

---

### 2️⃣ Remove Automatic Deployment

Under **Post-build Actions**, remove:

```text
Build other projects
```

configured with:

```text
project1-prod-deploy
```

---

### 3️⃣ Configure Manual Deployment

Click:

```text
Add Post-build Action
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

Navigate to:

```text
Project1-view
```

Verify the pipeline:

```text
project1-build
       ↓
project1-test-deploy
       ↓
project1-prod-deploy
```

---

### 5️⃣ Trigger Production Deployment Manually

Click the **▶ Run** button beside:

```text
project1-prod-deploy
```

in Build Pipeline View.

---

## ✅ Expected Output

### Console Output

```text
deploying to production environment
```

### Build Status

```text
project1-prod-deploy SUCCESS
```

---

## 🔍 Verification

✅ Production deployment does not start automatically

✅ Manual **▶ Run** button is required

✅ Deployment starts only after manual trigger

✅ Production deployment completes successfully

---

## 🎉 Conclusion

```text
Build
  ↓
Test
  ↓
Manual Approval
  ↓
Production Deployment
```

🚀 Production deployment requires manual approval before deployment.

---

# 📊 Continuous Deployment vs Continuous Delivery

| Feature | Continuous Deployment | Continuous Delivery |
|----------|----------------------|---------------------|
| Production Deployment | Automatic | Manual |
| Human Approval | ❌ Not Required | ✅ Required |
| Jenkins Configuration | Build other projects | Build other projects (manual step) |
| Deployment Trigger | Automatic | Manual Run Button |
| Goal | Fully Automated Deployment | Deployment Ready Anytime |

---

# 🎯 Final Summary

### Continuous Deployment

```text
Build
 ↓
Test
 ↓
Production
```

✅ Automatic Deployment

---

### Continuous Delivery

```text
Build
 ↓
Test
 ↓
Manual Approval
 ↓
Production
```

✅ Manual Deployment

The only difference is:

👉 **Automatic Production Deployment = Continuous Deployment**

👉 **Manual Production Deployment = Continuous Delivery**
