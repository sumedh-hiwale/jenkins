# 🚀 Jenkins Global Environment Variable Demo

## Step 1

- Click **New Item**
- Enter project name:

```text
demo-global-var-1
```

- Select **Freestyle Project**
- Click **OK**

---

## Step 2

- Click **Add Build Step**
- Select **Execute Shell**
- Add:

```bash
echo ${GLOBAL_VAR}
```

- Click **Save**

---

## Step 3

- Click **Build Now**
- Open **Console Output**
- Verify that no value is displayed for `GLOBAL_VAR`

---

## Step 4

- Click **New Item**
- Enter project name:

```text
demo-global-var-2
```

- In **Duplicate an existing item**, enter:

```text
demo-global-var-1
```

- Click **OK**
- Click **Save**

---

## Step 5

- Click **Build Now**
- Open **Console Output**
- Verify that no value is displayed for `GLOBAL_VAR`

---

## Step 6

- Go to **Manage Jenkins**
- Click **System**
- Scroll to **Global Properties**
- Enable **Environment Variables**
- Click **Add**
- Enter:

```text
Name  : GLOBAL_VAR
Value : mytestGlobalVar
```

- Click **Save**

---

## Step 7

- Open **demo-global-var-1**
- Click **Build Now**
- Open **Console Output**
- Verify that `mytestGlobalVar` is displayed

---

## Step 8

- Open **demo-global-var-2**
- Click **Build Now**
- Open **Console Output**
- Verify that `mytestGlobalVar` is displayed

---

## Verification

- `GLOBAL_VAR` was unavailable before configuration.
- After creating the Global Environment Variable, both jobs successfully accessed the same value.

---

## Output

```bash
+ echo mytestGlobalVar
mytestGlobalVar
Finished: SUCCESS
```

---

## Conclusion

- Global Environment Variables are configured from **Manage Jenkins → System → Global Properties**.
- Global variables are automatically available to all Jenkins jobs.
- Both jobs successfully accessed the value of `GLOBAL_VAR`.

🚀 Demo Completed Successfullya
