# 🚀 Jenkins Parameterized Job – Password Parameter and Multi-line String Parameter

## Objective

Configure an existing Jenkins parameterized job by adding a Password Parameter and a Multi-line String Parameter, then verify their values through Console Output.

## Steps

### 1. Open Jenkins Dashboard.

### 2. Click **demo-parameter-job**.

### 3. Click **Configure**.

### 4. Verify **This project is parameterized** is enabled.

### 5. Click **Add Parameter** → **Password Parameter**.

### 6. Enter:

* Name: `yourPasswordParam`
* Default Value: `mypassword`

### 7. Click **Add Parameter** → **Multi-line String Parameter**.

### 8. Enter:

* Name: `multiLineStringParam`

### 9. In **Default Value**, enter:

```text
this is sumedh1
this is sumedh2
this is sumedh3
```

### 10. In the **Execute Shell** build step, add:

```bash
echo "multiline ${multiLineStringParam}"
echo "yourPasswordParam ${yourPasswordParam}"
```

### 11. Click **Save**.

### 12. Click **Build with Parameters**.

### 13. Enter/select:

* name = `sumedh`
* myboolparam = `Checked`
* deployTO = `Test`
* yourPasswordParam = `mypassword`

### 14. In **multiLineStringParam**, enter:

```text
this is sumedh1
this is sumedh2
this is sumedh3
```

### 15. Click **Build**.

### 16. Open the latest build.

### 17. Click **Console Output**.

## Verification

Verify the following output:

```bash
Hello sumedh
myboolparam true
deployTO Test

multiline this is sumedh1
this is sumedh2
this is sumedh3

yourPasswordParam mypassword
```

Verify the build status:

```bash
Finished: SUCCESS
```

## Conclusion

Successfully configured and tested Password Parameter and Multi-line String Parameter in a Jenkins Parameterized Job.
