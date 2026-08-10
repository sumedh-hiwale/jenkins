# ⏱️ Jenkins Build Timeout Demo

## 🎯 Objective

Demonstrate how Jenkins automatically stops a build after a specified timeout period and how to mark the timed-out build as **FAILED**.

---

# 🚫 Demo 1: Abort Build After Timeout

## 📌 Create Freestyle Project

* Click **New Item**
* Enter Job Name: `demo-timeout`
* Select **Freestyle Project**
* Click **OK**

## ⚙️ Configure Build Timeout

Navigate to **Build Environment** and select:

```text
Terminate a build if it's stuck
```

Configure:

```text
Time-out Strategy : Absolute
Timeout Minutes   : 3
```

## 🖥️ Configure Build Step

Navigate to **Build** section.

Click:

```text
Add Build Step → Execute Shell
```

Enter:

```bash
sleep 240
```

Click **Save**.

## ▶️ Execute Job

* Click **Build Now**
* Wait approximately **3 minutes**

## ✅ Verification

Console Output:

```text
+ sleep 240
Build timed out (after 3 minutes)
Terminated
Build was aborted
Finished: ABORTED
Marking the build as aborted
```

## 🎉 Result

```text
Build Status = ABORTED
```

---

# ❌ Demo 2: Fail Build After Timeout

## ⚙️ Modify Existing Job

Open job:

```text
demo-timeout
```

Click **Configure**.

Navigate to **Build Environment**.

Click:

```text
Add Action
```

Select:

```text
Fail the build
```

Click **Save**.

## ▶️ Execute Job

* Click **Build Now**
* Wait approximately **3 minutes**

## ✅ Verification

Console Output:

```text
+ sleep 240
Build timed out (after 3 minutes)
Terminated
Finished: FAILURE
```

## 🎉 Result

```text
Build Status = FAILED
```

---

# 📊 Summary

| Configuration            | Result     |
| ------------------------ | ---------- |
| Timeout Only             | 🚫 ABORTED |
| Timeout + Fail the Build | ❌ FAILED   |

---

# 🏁 Conclusion

* ⏱️ Jenkins can automatically stop long-running builds using Build Timeout.
* 🚫 By default, a timed-out build is marked as **ABORTED**.
* ❌ Using **Fail the build** changes the final build status to **FAILED**.
* ✅ This helps enforce build execution limits and identify timeout failures clearly.
