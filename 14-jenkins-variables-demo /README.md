# 🚀 Jenkins Environment Variable

## Project Name

`demo-variable`

### Step 1

* Open Jenkins Dashboard.
* Click **New Item**.
* Enter project name: **demo-variable**.
* Select **Freestyle Project**.
* Click **OK**.

### Step 2

* Go to **Build Steps**.
* Click **Add Build Step → Execute Shell**.
* Add the following commands:

```bash
name=Gaurav
echo "Hello, My name is ${name}"
```

* Click **Save**.

### Step 3

* Click **Build Now**.
* Open **Console Output** and verify:

```text
Hello, My name is Gaurav
```

### Step 4

* Click **Configure**.
* In **Execute Shell**, append:

```bash
echo "Build Id is ${BUILD_ID}"
echo "Job name is ${JOB_NAME}"
```

* Click **Save**.

### Step 5

* Click **Build Now** again.
* Open **Console Output** and verify:

```text
Hello, My name is Gaurav
Build Id is 2
Job name is demo-variable
```

## Verification

* User-defined variable (`name`) printed successfully.
* Jenkins environment variable (`BUILD_ID`) printed successfully.
* Jenkins environment variable (`JOB_NAME`) printed successfully.
* Build completed with **SUCCESS** status. ✅

## Conclusion

* Created a user-defined variable.
* Used Jenkins built-in environment variables.
* Verified variable substitution during build execution.
* Build executed successfully.
