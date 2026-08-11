# 🚀 Pipeline as Code - Build Parameters

## 🎯 Objective

To demonstrate how Build Parameters can be used in a Jenkins Pipeline to accept user input during build execution.

---

## 📋 Prerequisites

- ✅ Jenkins Installed and Running
- ✅ Existing Pipeline Job Created
- ✅ Pipeline configured using Pipeline Script (Jenkinsfile)

---

## 🔧 Step 1: Open Existing Pipeline

1. Open the existing pipeline job:

   ```
   Pipeline-as-code-Hello-world
   ```

2. Click **⚙️ Configure**.

---

## 📝 Step 2: Add Build Parameters

Add the following parameters in the Jenkinsfile:

```groovy
parameters {
    string(
        name: 'person',
        defaultValue: 'unnati development',
        description: 'Who are you?'
    )

    booleanParam(
        name: 'isMale',
        defaultValue: true,
        description: 'Gender'
    )

    choice(
        name: 'city',
        choices: ['jaipur', 'mumbai', 'pune'],
        description: 'Select City'
    )
}
```

---

## 🖥️ Step 3: Display Parameter Values

Add a stage to print parameter values:

```groovy
stage('Parameters') {
    steps {
        echo "Person: ${params.person}"
        echo "Is Male: ${params.isMale}"
        echo "City: ${params.city}"
    }
}
```

💾 Save the pipeline configuration.

---

## ▶️ Step 4: Run Build With Parameters

Click:

```text
Build With Parameters
```

The following parameters will be displayed:

- 👤 person
- ☑️ isMale
- 🏙️ city

### Example Input

```text
person = Sumedh
isMale = true
city = mumbai
```

Click **🚀 Build**.

---

## 📄 Step 5: Verify Console Output

Expected output:

```text
Person: Sumedh
Is Male: true
City: mumbai
```

✅ This confirms that the pipeline successfully receives user input through build parameters.

---

## 🧪 Step 6: Test Boolean Parameter

Add a condition to the deployment stage:

```groovy
stage('Deploy on prod') {
    when {
        expression {
            params.isMale == true
        }
    }

    steps {
        echo 'Deploy on prod1'
    }
}
```

### ✅ Case 1: isMale = true

Output:

```text
Deploy on prod1
```

The stage executes successfully.

### ❌ Case 2: isMale = false

Output:

```text
Stage "Deploy on prod" skipped due to when condition
```

The stage is skipped because the condition evaluates to false.

---

## 🔍 Observation

After adding a new parameter to the Jenkinsfile:

1. 💾 Save the pipeline.
2. ▶️ Run the pipeline once.
3. 🔄 Open **Build With Parameters** again.

✅ The newly added parameter becomes visible.

> ℹ️ This is normal Jenkins behavior.

---

## 📚 Parameter Types Demonstrated

### 👤 String Parameter

```groovy
string(name: 'person')
```

Used to accept text input from the user.

---

### ☑️ Boolean Parameter

```groovy
booleanParam(name: 'isMale')
```

Used for True/False or Yes/No selections.

---

### 🏙️ Choice Parameter

```groovy
choice(name: 'city', choices: ['jaipur','mumbai','pune'])
```

Used to select a value from a predefined list.

---

## 🔑 Accessing Parameter Values

Parameters can be accessed using:

```groovy
params.person
params.isMale
params.city
```

---

## 🎉 Conclusion

Build Parameters allow users to provide input at build time, making Jenkins pipelines:

- ⚡ Dynamic
- ♻️ Reusable
- 🎛️ Configurable

In this demo, the following parameter types were successfully configured and used:

- 👤 String Parameter
- ☑️ Boolean Parameter
- 🏙️ Choice Parameter
