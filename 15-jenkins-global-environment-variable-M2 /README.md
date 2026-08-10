# 🚀 Jenkins Global Environment Variable Demo

## Objective

Create a Global Environment Variable in Jenkins and access it from a Jenkins Freestyle Project.

## Step 1: Create Global Environment Variable

* Go to **Manage Jenkins**
* Click **System**
* Scroll to **Global Properties**
* Enable **Environment Variables**
* Click **Add**

Enter the following values:

```text
Name  : GLOBAL_VAR
Value : mytestGlobalVar
```

* Click **Save**

---

## Step 2: Create Freestyle Project

* Click **New Item**
* Enter project name:

```text
demo-global-var
```

* Select **Freestyle Project**
* Click **OK**

---

## Step 3: Configure Build Step

* Click **Add Build Step**
* Select **Execute Shell**
* Add the following command:

```bash
echo ${GLOBAL_VAR}
```

* Click **Save**

---

## Step 4: Build the Job

* Click **Build Now**

---

## Step 5: Verify Console Output

* Open **Console Output**

Expected Output:

```bash
+ echo mytestGlobalVar
mytestGlobalVar
Finished: SUCCESS
```

---

## Verification

* Global Environment Variable was created successfully.
* Jenkins job accessed the variable without defining it inside the job.
* The configured value was displayed in the console output.

## Conclusion

* Global Environment Variables are configured from:

```text
Manage Jenkins
└── System
    └── Global Properties
        └── Environment Variables
```

* Once configured, the variable becomes available to Jenkins jobs.
* `GLOBAL_VAR=mytestGlobalVar` was successfully accessed from the Freestyle Project.
