# 🚀 Execute Concurrent Builds if Necessary

## 📌 Job Details

**Job Name:** `demo-concurrent`

---

## 📝 Steps

1. Go to **Jenkins Dashboard** → Click **New Item**.
2. Enter Job Name: **demo-concurrent**.
3. Select **Freestyle project** → Click **OK**.
4. Scroll down and enable **Execute concurrent builds if necessary**.
5. Go to **Build Steps** → **Add build step** → **Execute shell**.
6. Enter the following command:

```bash
sleep 15
```

7. Click **Save**.
8. Open the job **demo-concurrent**.
9. Click **Build Now** 3–4 times quickly.
10. Open **Build Executor Status** from Jenkins Dashboard.

---

## 🎯 Expected Output

- Multiple builds run simultaneously for 15 seconds.
- Build #1, Build #2, Build #3 start without waiting in the queue.
- All builds complete successfully.

---

## ✅ Verification

- Verify multiple builds are visible in **Build History**.
- Verify multiple executors are running the same job in **Build Executor Status**.
- Verify builds are not waiting in the queue.
- Verify all builds complete with **Success** status.

---

## 💡 Note

🔹 **Option OFF** → One build starts only after the previous build has finished.

🔹 **Option ON** → Multiple builds of the same job can run simultaneously (if executors are available). ✅

---
