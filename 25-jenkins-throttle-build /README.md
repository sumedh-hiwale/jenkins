# 🚀🚦 Jenkins Throttle Build Demo

## 🎯 Objective

Demonstrate how to limit the number of builds executed within a specific time period using the **Throttle Builds** option.

---

## 📝 Steps

### 1️⃣ Create a New Job
- Click **New Item**
- Enter Job Name: `demo-throttle`
- Select **Freestyle Project**
- Click **OK**

### 2️⃣ Configure Throttle Builds
- Click **Configure**
- Enable **Throttle builds**
- Set:
  - **Number of builds:** `3`
  - **Time period:** `Minute`

### 3️⃣ Add Build Step
- Click **Add Build Step** → **Execute Shell**
- Enter:

```bash
echo "Hello World"
```

### 4️⃣ Save the Job
- Click **Save**

### 5️⃣ Trigger Builds
- Click **Build Now** multiple times continuously.

### 6️⃣ Check Console Output
- Open a build number.
- Click **Console Output**.

---

## 📌 Expected Output

```text
Hello World
Finished: SUCCESS
```

---

## ✅ Verification

- Verify the job is created successfully.
- Verify **Throttle builds** is enabled.
- Verify the build executes successfully.
- Verify the Console Output displays:

```text
Hello World
```

- Verify the build status is:

```text
SUCCESS
```

---

## 🎉 Conclusion

Successfully configured and tested **Throttle Builds** in Jenkins. The job executed successfully and displayed the expected output in the Console Output.
