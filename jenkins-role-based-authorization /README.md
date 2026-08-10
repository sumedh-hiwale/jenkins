# 🚀 Jenkins Role-Based Authorization Strategy

## Steps

1. Manage Jenkins → Plugins → Install **Role-Based Authorization Strategy** Plugin

2. Restart Jenkins

```bash
sudo systemctl restart jenkins
```

3. Manage Jenkins → Security → Authorization → Select **Role-Based Strategy** → Save

4. Manage Jenkins → Users → Create User

   * Username: `sumedh`

5. Manage Jenkins → Manage and Assign Roles → Manage Roles

   * Role Name: `developer-role`
   * Permissions:

     * Overall → Read ✅
     * Job → Read ✅

6. Manage Jenkins → Manage and Assign Roles → Assign Roles

   * Add User
   * User ID: `sumedh`
   * Select Role: `developer-role`

7. Click **Save**

## Verification

* Login as `sumedh`
* Dashboard Accessible ✅
* View Jobs ✅
* Build Jobs ❌
* Configure Jobs ❌
* Delete Jobs ❌
* Manage Jenkins ❌

---

# 🚀 If User Should Only Be Able to Build Jobs

## Steps

1. Manage Jenkins → Manage and Assign Roles → Manage Roles

2. Edit `developer-role`

3. Assign Permissions:

   * Overall → Read ✅
   * Job → Read ✅
   * Job → Build ✅

4. Click **Save**

## Verification

* Login as `sumedh`
* View Jobs ✅
* Build Jobs ✅
* Configure Jobs ❌
* Delete Jobs ❌
* Manage Jenkins ❌
