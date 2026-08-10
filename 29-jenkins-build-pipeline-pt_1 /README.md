# 🚀 Create First Jenkins Pipeline Using Build Pipeline Plugin

## 🎯 Objective

Create a simple Jenkins Build Pipeline using the **Build Pipeline Plugin**, where the `project1-build` job automatically triggers the `project1-test-deploy` job after a successful build.

---

## 🛠 Prerequisites

- Jenkins Installed
- Administrator Access
- Build Pipeline Plugin Installed

---

## 📝 Step 1: Create Build Job

- Click **New Item**
- Enter Job Name: `project1-build`
- Select **Freestyle Project**
- Click **OK**

### Configure Build Step

**Build → Execute Shell**

```bash
sleep 10
echo "project is building"
```

- Click **Save**

---

## 📝 Step 2: Create Test/Deploy Job

- Click **New Item**
- Enter Job Name: `project1-test-deploy`
- Select **Freestyle Project**
- Click **OK**

### Configure Build Step

**Build → Execute Shell**

```bash
sleep 10
echo "deploying to testing enviroment"
```

- Click **Save**

---

## 🔌 Step 3: Install Build Pipeline Plugin

- Go to **Manage Jenkins**
- Click **Plugins**
- Open **Available Plugins**
- Search for **Build Pipeline**
- Install the plugin
- Restart Jenkins if required

---

## 🔗 Step 4: Configure Downstream Job Trigger

Open Job:

`project1-build`

Navigate to:

**Post Build Actions → Add Post-build Action**

Select:

**Build other projects**

Configure:

```text
Projects to build:
project1-test-deploy
```

Enable:

```text
✅ Trigger only if build is stable
```

- Click **Save**

---

## 👁️ Step 5: Create Build Pipeline View

- From Jenkins Dashboard click **➕**
- Enter View Name:

```text
Project1-view
```

- Select:

```text
Build Pipeline View
```

- Click **OK**

---

## ⚙️ Step 6: Configure Pipeline View

Set:

```text
Select Initial Job:
project1-build
```

- Click **Save**

---

## ▶️ Step 7: Run the Pipeline

- Open **Project1-view**
- Click **Run**

---

## 🔄 Pipeline Flow

```text
project1-build
        │
        ▼
project1-test-deploy
```

---

## 📊 Expected Output

### Build Job Output

```text
project is building
```

### Test/Deploy Job Output

```text
deploying to testing enviroment
```

---

## 📸 Output

After clicking **Run**, Jenkins successfully executed both jobs in sequence.

```text
🟢 project1-build
        │
        ▼
🟢 project1-test-deploy
```

Both jobs completed successfully and appeared in **Green (SUCCESS)** status in the Build Pipeline View.

---

## ✅ Verification

- Verify Build Pipeline Plugin is installed.
- Verify `project1-build` executes successfully.
- Verify `project1-test-deploy` is triggered automatically.
- Verify both jobs show **SUCCESS** status.
- Verify Build Pipeline View displays the complete workflow.
- Verify the upstream and downstream job relationship is visible.

---

## 🎉 Result

Successfully created a Jenkins Build Pipeline using the **Build Pipeline Plugin**.

The `project1-build` job executed first and automatically triggered the `project1-test-deploy` job after a successful build. The Build Pipeline View visually displayed the complete workflow and confirmed successful execution of both stages. 🚀
