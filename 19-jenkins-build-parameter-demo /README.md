#  🚀📁 Jenkins File Parameter Demo

## 🎯 Objective

Demonstrate how to use the **File Parameter** in a Jenkins Freestyle Project to upload a file during build execution and read its contents using a shell command.

---

## 🛠️ Steps

### 1️⃣ Create a Freestyle Project

* Open **Jenkins Dashboard**
* Click **New Item**
* Enter project name: `demo-file-param`
* Select **Freestyle Project**
* Click **OK**

### 2️⃣ Configure File Parameter

* Enable **This project is parameterized**
* Click **Add Parameter** → **File Parameter**
* Set:

```text
File Location: filePath
```

### 3️⃣ Add Build Step

* Click **Add Build Step** → **Execute Shell**
* Enter:

```bash
cat filePath
```

* Click **Save**

### 4️⃣ Create a Test File on Jenkins Server

Open the terminal where Jenkins is installed and run:

```bash
echo "this is testfile" > test.txt
cat test.txt
```

### 5️⃣ Build the Job

* Open the **demo-file-param** job
* Click **Build with Parameters**
* Click **Choose File**

### 6️⃣ Understand the File Selection Behavior

⚠️ **Important**

The **Choose File** option opens the file manager of your **local computer**, not the Jenkins server (AWS/EC2).

Because the `test.txt` file was created on the Jenkins server, it is **not visible** in the local computer file manager and cannot be selected directly.

### 7️⃣ Create a Local File

To upload a file using the File Parameter:

* Open **Notepad** on your local computer
* Enter:

```text
this is testfile
```

* Save the file as:

```text
test.txt
```

### 8️⃣ Upload the File

* Return to Jenkins
* Click **Choose File**
* Select the locally created **test.txt**
* Click **Build**

### 9️⃣ Verify the Output

* Open **Console Output**
* Verify that Jenkins displays:

```text
this is testfile
```

---

## ✅ Verification

* File Parameter successfully accepted the uploaded file.
* Jenkins stored the uploaded file at `filePath`.
* The `cat filePath` command displayed the uploaded file content.
* Files created on the Jenkins server are not visible in the local computer file chooser.
* Files created on the local computer can be uploaded and used during build execution.

---

## 📚 Key Learning

```text
Local File
    │
    ▼
Choose File
    │
    ▼
Jenkins Uploads File
    │
    ▼
filePath
    │
    ▼
cat filePath
    │
    ▼
Console Output
```

💡 **File Parameter always expects a file from the machine where the browser is running (your local computer).**
