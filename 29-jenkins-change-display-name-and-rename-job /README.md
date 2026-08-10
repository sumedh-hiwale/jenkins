# 🚀 Jenkins Change Display Name and Rename Job Demo

## 🎯 Objective
Demonstrate the difference between **Display Name** and **Rename Job** in Jenkins.

---

## 🛠️ Prerequisites

- Jenkins Installed
- Access to Jenkins Dashboard
- Permission to create and modify jobs

---

## 📝 Demo Steps

### 1️⃣ Create a Freestyle Job

- Click **New Item**
- Enter Job Name: `demo-3`
- Select **Freestyle Project**
- Click **OK**
- Click **Save**

---

### 2️⃣ Change the Display Name

- Open the `demo-3` job
- Click **Configure**
- Navigate to **General → Advanced**
- Enable **Display Name**
- Enter:

```text
DEMO-THREE
```

- Click **Save**

---

### 3️⃣ Verify the Display Name

- Return to the Jenkins Dashboard

✅ The job is now displayed as:

```text
DEMO-THREE
```

- Open the job

You will notice:

```text
Project name: demo-3
```

✅ Only the Display Name has changed.

❌ The actual Project Name remains unchanged.

---

### 4️⃣ Rename the Job

- Open the job
- Click **Rename** from the left menu
- Enter the new name:

```text
demo-3rd-yt
```

- Click **Rename**

---

### 5️⃣ Verify the Job Rename

- Open the renamed job

Verify:

```text
Project name: demo-3rd-yt
```

✅ The actual Jenkins Job Name has been updated successfully.

---

## 📌 Expected Output

### After Changing Display Name

```text
Dashboard Name : DEMO-THREE
Project Name   : demo-3
```

### After Renaming the Job

```text
Dashboard Name : DEMO-THREE
Project Name   : demo-3rd-yt
```

---

## ✅ Verification

- ✔️ Display Name changed successfully.
- ✔️ Original Project Name remained unchanged after changing Display Name.
- ✔️ Rename option changed the actual Jenkins Job Name.
- ✔️ Dashboard Name and Project Name can be different.

---

## 🎉 Conclusion

This demo demonstrates the difference between:

🔹 **Display Name** → Changes only the name displayed on the Jenkins Dashboard.

🔹 **Rename Job** → Changes the actual Jenkins Project Name.

Both features can be used independently depending on your requirements.
