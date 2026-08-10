# 🚀 Jenkins - Build Periodically Demo

---

## 🎯 Objective

Demonstrate how to automatically trigger a Jenkins job at regular intervals using the **Build periodically** option.

---

## 📋 Prerequisites

* Jenkins Server Installed
* Freestyle Project Creation Access

---

## ⚙️ Step 1: Create a Freestyle Project

1. Click **New Item**.

2. Enter the project name:

   ```text
   demo-period-build
   ```

3. Select **Freestyle Project**.

4. Click **OK**.

---

## ⚙️ Step 2: Configure Build Step

1. Open **demo-period-build** → **Configure**.
2. Navigate to **Build Steps**.
3. Click **Add Build Step** → **Execute Shell**.
4. Enter the following command:

   ```bash
   date
   ```

---

## ⚙️ Step 3: Configure Periodic Build Trigger

1. Navigate to **Build Triggers**.

2. Enable:

   ```text
   Build periodically
   ```

3. In the **Schedule** field, enter:

   ```text
   */1 * * * *
   ```

4. Click **Save**.

---

## ▶️ Step 4: Wait for Automatic Execution

1. Open the job dashboard.
2. Wait for approximately one minute.
3. Jenkins automatically triggers the job based on the configured schedule.

---

## 🔍 Verification

### Build History

Verify that a new build is created automatically every minute.

### Console Output

Open any build and click **Console Output**.

Expected Output:

```bash
Tue Jun 08 10:45:01 UTC 2026
Tue Jun 08 10:46:01 UTC 2026
Tue Jun 08 10:47:01 UTC 2026
```

---

## 🔄 Build Flow

```text
Build Periodically Enabled
            ↓
Cron Schedule: */1 * * * *
            ↓
Job Triggers Every 1 Minute
            ↓
Execute Shell Runs
            ↓
date Command Executes
            ↓
New Build Created Automatically
```

---

## ⏰ Cron Schedule Explanation

```text
*/1 * * * *
```

| Field        | Value | Description           |
| ------------ | ----- | --------------------- |
| Minute       | */1   | Every 1 Minute        |
| Hour         | *     | Every Hour            |
| Day of Month | *     | Every Day             |
| Month        | *     | Every Month           |
| Day of Week  | *     | Every Day of the Week |

---

## ✅ Result

The **demo-period-build** job is automatically triggered every **1 minute** using the **Build periodically** option and executes the `date` command during each build.
