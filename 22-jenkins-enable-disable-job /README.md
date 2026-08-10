# 🚀🚦 Jenkins Enable/Disable Job Demo

## 🎯 Objective

Demonstrate how to enable and disable a Jenkins job.

---

## 🛠️ Steps

### 🔴 Disable Job

1. Open **Jenkins Dashboard**.
2. Open the **demo-first** job.
3. Click **Configure**.
4. In the **General** section, turn the **Enabled** toggle **OFF**.
5. Click **Save**.

### 🟢 Enable Job

1. Open the **demo-first** job.
2. Click **Configure**.
3. In the **General** section, turn the **Enabled** toggle **ON**.
4. Click **Save**.

---

## 🎯 Expected Output

### After Disabling

- Job status changes to **Disabled**.
- **Build Now** option is unavailable.
- Manual job execution is blocked.

### After Enabling

- Job becomes active again.
- **Build Now** option is available.
- Job can be executed successfully.

---

## ✅ Verification

- Verify that **Build Now** disappears after disabling the job.
- Verify that **Build Now** reappears after enabling the job.
- Run a build successfully after enabling the job.

---

## 🏁 Conclusion

Successfully demonstrated how to **Disable** and **Enable** a Jenkins job using the **Enabled** toggle available in the job configuration page.
