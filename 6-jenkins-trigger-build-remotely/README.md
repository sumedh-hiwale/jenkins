# 🚀 Jenkins - Trigger Build Remotely

## Objective
Trigger a Jenkins build remotely using a URL and token.

## Steps

1. Open Jenkins Dashboard

2. Select Job → Configure

3. Go to Build Triggers

4. Enable **Trigger builds remotely (e.g., from scripts)**

5. Enter Token

   ```text
   mytoken123
   ```

6. Click Save

7. Trigger Build

   ```bash
   http://<JENKINS_URL>/job/<JOB_NAME>/build?token=mytoken123
   ```

8. Verify Build History

## Result

Remote build triggering is configured successfully.
