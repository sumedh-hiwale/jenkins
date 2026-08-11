# 🚀 Assign a Job to Jenkins Slave Using Labels

## 📌 Objective

Assign a specific Jenkins job to a specific Jenkins Agent (Slave) using Labels.

---

## 🛠️ Prerequisites

* Jenkins Server Running
* Jenkins Agent Connected
* Agent Name:

  ```text
  Linux-Slave
  ```
* Agent Label:

  ```text
  linux
  ```

---

## 📋 Step 1: Verify Agent Label

Navigate to:

```text
Manage Jenkins
→ Nodes
→ Linux-Slave
→ Configure
```

Verify the Label:

```text
linux
```

Save if required.

---

## 📋 Step 2: Create a Freestyle Job

1. Click **New Item**
2. Enter Job Name:

```text
Linux-Machine-Job
```

3. Select **Freestyle Project**
4. Click **OK**

---

## 📋 Step 3: Add Build Commands

1. Click **Configure**
2. Scroll to **Build**
3. Click **Add Build Step**
4. Select **Execute Shell**
5. Add the following commands:

```bash
echo "Hello World"
sleep 10
```

---

## 📋 Step 4: Restrict Job to Linux Agent

Under **General**:

✅ Enable:

```text
Restrict where this project can be run
```

Enter the Label Expression:

```text
linux
```

Click **Save**

---

## 📋 Step 5: Build the Job

1. Click **Build Now**
2. Open **Build History**
3. Open **Console Output**

---

## ✅ Expected Output

```text
Started by user admin
Running as SYSTEM

Building remotely on Linux-Slave (linux)

+ echo Hello World
Hello World

+ sleep 10

Finished: SUCCESS
```

---

## 🔍 Verification

Verify the following line exists in the Console Output:

```text
Building remotely on Linux-Slave (linux)
```

This confirms that Jenkins matched the label **linux** and executed the job on the **Linux-Slave** node.

---

## 🎯 Conclusion

Successfully assigned a Jenkins job to a specific Jenkins Agent using Labels.

* 🖥️ Job: `Linux-Machine-Job`
* 🏷️ Label: `linux`
* 🤖 Agent: `Linux-Slave`

The job will now run only on nodes that have the label **linux**.
