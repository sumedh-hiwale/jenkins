# 🚀 Jenkins - Trigger Even if the Build is Unstable (3rd option)


---

## 🎯 Objective

Demonstrate how a downstream Jenkins job can be triggered automatically when the upstream job finishes with an **UNSTABLE** status.

---

## 📋 Prerequisites

* Jenkins Server Installed
* Two Freestyle Jobs Created:

  * demo-4th (Upstream Job)
  * demo-5th (Downstream Job)

---

## ⚙️ Step 1: Configure Downstream Job (demo-5th)

1. Open **demo-5th** → **Configure**.

2. Navigate to **Build Triggers**.

3. Enable:

   ```
   Build after other projects are built
   ```

4. In **Projects to watch**, enter:

   ```
   demo-4th
   ```

5. Enable:

   ```
   Trigger even if the build is unstable
   ```

6. Click **Save**.

---

## ⚙️ Step 2: Configure Upstream Job (demo-4th)

1. Open **demo-4th** → **Configure**.

2. Go to **Build Steps**.

3. Add an **Execute Shell** build step.

4. Enter the following command:

   ```bash
   exit 10
   ```

5. Click **Advanced** under Execute Shell.

6. In **Exit code to set build unstable**, enter:

   ```
   10
   ```

7. Click **Save**.

---

## ▶️ Step 3: Trigger the Upstream Job

1. Open **demo-4th**.
2. Click **Build Now**.
3. Wait for the build to complete.

---

## 🔍 Verification

### Upstream Job Status

```
demo-4th → UNSTABLE ⚠️
```

### Downstream Job Status

```
demo-5th → Triggered Automatically ✅
```

---

## 🔄 Build Flow

```text
demo-4th (UNSTABLE)
          ↓
demo-5th (TRIGGERED)
```

---

## ✅ Result

When **"Trigger even if the build is unstable"** is enabled in **demo-5th**, Jenkins automatically triggers **demo-5th** whenever **demo-4th** completes with an **UNSTABLE** build status.
