# 🚀⏱️ Jenkins Console Output Timestamp Demo

## 🎯 Objective

Display timestamps for each line in the Jenkins Console Output.

## 📋 Steps

1. Open **Jenkins Dashboard**.
2. Click **New Item**.
3. Enter the job name **demo-timestamp**.
4. Select **Freestyle Project**.
5. Click **OK**.
6. In the **Build Environment** section, enable **Add timestamps to the Console Output**.
7. In the **Build Steps** section, click **Add Build Step** → **Execute Shell**.
8. Enter the following commands:

```bash
echo "this is first line"
sleep 3
echo "2nd line"
```

9. Click **Save**.
10. Click **Build Now**.
11. Open the latest build from **Build History**.
12. Click **Console Output**.

## 📤 Expected Output

```text
14:34:03 + echo this is first line
14:34:03 this is first line
14:34:03 + sleep 3
14:34:06 + echo 2nd line
14:34:06 2nd line
14:34:06 Finished: SUCCESS
```

## ✅ Verification

- Timestamp is displayed at the beginning of each console output line.
- The `sleep 3` command creates a 3-second gap between timestamps.
- Console logs show the exact execution time of each command.
- The build completes successfully.

## 🎉 Result

- Jenkins successfully added timestamps to the console output.
- Command execution timing is clearly visible in the build logs.
- The build finished with **SUCCESS** status.
