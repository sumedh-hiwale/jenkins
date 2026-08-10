# 🚀 Jenkins Installation on Ubuntu

## 🎯 Objective

Install Jenkins on an Ubuntu server using the official Jenkins repository and configure it to start automatically after system reboot.

---

## 📋 Prerequisites

* Ubuntu Server
* User with sudo privileges
* Internet connectivity
* Minimum 2 GB RAM recommended

---

## 🛠️ Step 1: Update System Packages

Update the package repository before installing software.

```bash
sudo apt update
```

---

## ☕ Step 2: Install Java

Jenkins requires Java to run.

```bash
sudo apt install fontconfig openjdk-21-jre
```

Verify Java installation:

```bash
java -version
```

Expected Output:

```bash
openjdk version "21.x.x"
```

---

## 🔑 Step 3: Add Jenkins Repository Key

Download and add the Jenkins GPG key.

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```

---

## 📦 Step 4: Add Jenkins Repository

Add the official Jenkins package repository.

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

---

## 🔄 Step 5: Update Package Index

Refresh package information after adding the Jenkins repository.

```bash
sudo apt update
```

---

## 📥 Step 6: Install Jenkins

Install Jenkins package.

```bash
sudo apt install jenkins
```

---

## ▶️ Step 7: Start Jenkins Service

Start the Jenkins service.

```bash
sudo systemctl start jenkins
```

---

## 🔁 Step 8: Enable Jenkins Service

Enable Jenkins to start automatically on system boot.

```bash
sudo systemctl enable jenkins
```

---

## ✅ Step 9: Verify Jenkins Status

Check whether Jenkins is running successfully.

```bash
sudo systemctl status jenkins
```

Expected Output:

```bash
Active: active (running)
```

---

## 🌐 Step 10: Access Jenkins Web UI

Open your browser and access Jenkins:

```text
http://<SERVER-IP>:8080
```

Example:

```text
http://54.xx.xx.xx:8080
```

---

## 🔓 Step 11: Retrieve Initial Admin Password

Jenkins generates an initial password during installation.

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password and paste it into the Jenkins setup page.

---

## 🎉 Installation Complete

Jenkins has been successfully installed and configured on Ubuntu.

### Verification Checklist

✅ Java Installed

✅ Jenkins Repository Added

✅ Jenkins Installed

✅ Jenkins Service Running

✅ Auto Start Enabled

✅ Jenkins Web UI Accessible

---

## 📚 Useful Commands

### Check Jenkins Status

```bash
sudo systemctl status jenkins
```

### Start Jenkins

```bash
sudo systemctl start jenkins
```

### Stop Jenkins

```bash
sudo systemctl stop jenkins
```

### Restart Jenkins

```bash
sudo systemctl restart jenkins
```

### View Jenkins Logs

```bash
sudo journalctl -u jenkins -f
```

---

## 🏁 Conclusion

In this project, Jenkins was installed on an Ubuntu server using the official Jenkins repository. Java was configured, Jenkins service was enabled, and the Jenkins web dashboard was successfully made accessible for CI/CD pipeline creation and automation tasks.
