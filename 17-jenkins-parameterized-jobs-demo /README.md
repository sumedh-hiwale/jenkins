# 🚀 Jenkins Parameterized Jobs Demo

## Objective

Demonstrate the use of Parameterized Jobs in Jenkins using String, Boolean, and Choice Parameters.

---

## Steps

### 1. Create Jenkins Job

1. Create a new **Freestyle Project** named **demo-parameter-job**.
2. Click **OK**.

### 2. Configure Execute Shell

1. Go to **Build Steps → Add Build Step → Execute Shell**.
2. Add the following command:

```bash
echo "Hello ${name}"
```

3. Click **Save**.

### 3. Run Initial Build

1. Click **Build Now**.
2. Open **Console Output**.

Output:

```bash
Hello
Finished: SUCCESS
```

### 4. Add String Parameter

1. Click **Configure**.
2. Enable **This project is parameterized**.
3. Click **Add Parameter → String Parameter**.
4. Enter:

```text
Name: name
Default Value: sumedh
```

5. Click **Save**.

> After enabling parameterization, **Build Now** automatically changes to **Build With Parameters** because Jenkins requires parameter values before starting the build.

### 5. Build Using String Parameter

1. Click **Build With Parameters**.
2. Enter:

```text
name = sumedh
```

3. Click **Build**.

Output:

```bash
Hello sumedh
Finished: SUCCESS
```

### 6. Add Boolean Parameter

1. Click **Configure**.
2. Click **Add Parameter → Boolean Parameter**.
3. Enter:

```text
Name: myboolparam
Set by Default: Checked
```

### 7. Add Choice Parameter

1. Click **Add Parameter → Choice Parameter**.
2. Enter:

```text
Name: deployTO
```

Choices:

```text
Test
QA
PreProd
Prod
```

### 8. Update Execute Shell Script

Append the following commands:

```bash
echo "Hello ${name}"
echo "myboolparam ${myboolparam}"
echo "deployTO ${deployTO}"
```

3. Click **Save**.

### 9. Build With Parameters

1. Click **Build With Parameters**.
2. Enter/Select:

```text
name = sumedh
myboolparam = checked
deployTO = PreProd
```

3. Click **Build**.

### 10. Verification

Console Output:

```bash
Hello sumedh
myboolparam true
deployTO PreProd
Finished: SUCCESS
```

---

## Result

Successfully demonstrated Jenkins Parameterized Jobs using:

* String Parameter
* Boolean Parameter
* Choice Parameter

and passed parameter values to an Execute Shell build step.
