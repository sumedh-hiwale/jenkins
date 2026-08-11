# 🚀 Jenkins Slave (Agent) Installation & Setup on AWS EC2

## 📌 Objective

Configure a new Ubuntu EC2 instance as a Jenkins Agent (Slave) and connect it to the Jenkins Master using SSH.

---

## 🖥️ Step 1: Launch New EC2 Instance

Create a new Ubuntu EC2 instance.

```text
Instance Name = jenkins-agent
```

---

## 👤 Step 2: Create Agent User

Login to the Agent machine and create a user.

```bash
sudo adduser jenkins-slave-user
```

Set Password:

```text
1
```

---

## ⚙️ Step 3: Create New Node in Jenkins

Navigate to:

```text
Manage Jenkins
→ Nodes
→ New Node
```

Enter:

```text
Node Name = Linux-Slave
Select = Permanent Agent
```

Click:

```text
Create
```

---

## 🔧 Step 4: Configure Node

```text
Description = Linux Node

# of Executors = 2

Remote Root Directory = /home/jenkins-slave-user/jenkins

Labels = Linux

Usage = Use this node as much as possible

Launch Method = Launch agents via SSH

Host = <Agent Private IP>
```

Example:

```text
Host = 10.113.115.88
```

---

## 🔑 Step 5: Add Credentials

Navigate to:

```text
Credentials
→ Add
→ Username with password
```

Enter:

```text
Username = jenkins-slave-user

Password = 1

ID = sshDetails

Description = sshDetails
```

Click:

```text
Create
```

---

## ✅ Step 6: Select Credential

Select:

```text
jenkins-slave-user/****** (sshDetails)
```

---

## ⚙️ Step 7: Configure Remaining Settings

```text
Host Key Verification Strategy =
Non verifying Verification Strategy

Availability =
Keep this agent online as much as possible
```

Click:

```text
Save
```

---

## 🔓 Step 8: Enable Password Authentication

Login to Agent Machine:

```bash
sudo vi /etc/ssh/sshd_config
```

Update:

```text
PasswordAuthentication yes
```

Restart SSH Service:

```bash
sudo systemctl restart ssh
```

---

## ☕ Step 9: Install Java

```bash
sudo apt update

sudo apt install openjdk-21-jdk -y
```

Verify:

```bash
java -version
```

---

## 🚀 Step 10: Launch Agent

Navigate to:

```text
Nodes
→ Linux-Slave
→ Launch Agent
```

---

## 🎯 Expected Output

```text
Linux-Slave Connected
```

---

## 🔍 Verification

Navigate to:

```text
Manage Jenkins
→ Nodes
→ Linux-Slave
```

Verify:

```text
Status = Connected
```

---

## ✅ Conclusion

Successfully configured an Ubuntu EC2 instance as a Jenkins Agent (Slave), connected it to Jenkins Master using SSH, installed Java, and verified that the Agent is online and ready to execute Jenkins jobs.
