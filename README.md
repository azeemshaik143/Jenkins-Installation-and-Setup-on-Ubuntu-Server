# Jenkins-Installation-and-Setup-on-Ubuntu-Server

This guide explains how to **install Jenkins** on an **Ubuntu server**, **create a Jenkins user**, and **set up your first job**.

---

## 🧰 Prerequisites

Before you begin, ensure you have:

#An AWS EC2 instance (t2.micro or larger) running Ubuntu.

#SSH access to the instance.

#sudo privileges.

#Port 8080 open in the Security Group (for Jenkins web access).

---
<img width="1347" height="618" alt="1" src="https://github.com/user-attachments/assets/f18f70b2-c2f6-48a9-a078-e78f3792cb0d" />
<img width="1356" height="594" alt="2" src="https://github.com/user-attachments/assets/9dce056e-9d80-454a-a280-5aa43ed24837" />
<img width="1354" height="617" alt="3" src="https://github.com/user-attachments/assets/dd62eaa8-8998-4a53-9d71-75b2e59048cc" />
<img width="1359" height="602" alt="4" src="https://github.com/user-attachments/assets/31809ea8-8a35-4627-948f-106df66ef247" />
<img width="1153" height="625" alt="5" src="https://github.com/user-attachments/assets/06a121b0-9ff6-447a-a6f8-0042fd0f3df6" />
<img width="1249" height="391" alt="6" src="https://github.com/user-attachments/assets/78f00020-fc19-478f-b665-0d1081c47c2b" />


## ⚙️ Step 1: Update System Packages

```bash
sudo apt update
sudo apt install openjdk-21-jdk -y
java -version
````
<img width="1200" height="211" alt="7" src="https://github.com/user-attachments/assets/035c2aec-b971-49e9-a4e9-21efdff00882" />
<img width="959" height="231" alt="8" src="https://github.com/user-attachments/assets/95927361-0322-4b5f-9270-dcf41dd2aa6e" />
<img width="926" height="123" alt="9" src="https://github.com/user-attachments/assets/5cae42d1-4c7c-40e5-b3ca-acacdd276ce5" />


## 📦 Step 2: Add Jenkins Repository and Key

1. Add the Jenkins Debian repository key:

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```
<img width="886" height="176" alt="10" src="https://github.com/user-attachments/assets/a244ca13-ec1f-4e4d-9ed9-c8014ee6fadb" />


---

## ▶️ Step 3: Start and Enable Jenkins Service

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
```
<img width="1210" height="323" alt="10 5" src="https://github.com/user-attachments/assets/ecc0f280-2dbd-4b7f-a5f4-436095b9bd30" />

## 🔐 Step 4: Access Jenkins Web Interface

1. Open your browser and go to:

   ```
   http://16.171.141.172:8080
   ```
<img width="1236" height="704" alt="11" src="https://github.com/user-attachments/assets/dbee3029-0858-4351-8836-f88ef22bece0" />

2. Retrieve the initial admin password:

   ```bash
   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   ```
<img width="872" height="93" alt="12" src="https://github.com/user-attachments/assets/80694c28-364d-4d93-855d-972761dfc762" />

3. Copy the password and paste it into the Jenkins setup page.
<img width="1273" height="660" alt="13" src="https://github.com/user-attachments/assets/3c6f0ccf-2c89-462b-910c-a5d0af47f5b5" />
<img width="1224" height="639" alt="14" src="https://github.com/user-attachments/assets/b6b33a9a-50e5-486b-9013-9af8fd5670de" />


---

## 👤 Step 5: Create a Jenkins User

1. After installation, go to:

   * **Manage Jenkins → Security → Users**
   * Click **Create User**

2. Fill in the following fields:

   * Username: `admin`
   * Password: `*****`
   * Full Name: `admin`
   * Email: `admin@example.com`

3. Click **Create User**.

Alternatively, you can create users via Jenkins CLI later.
<img width="1229" height="678" alt="15" src="https://github.com/user-attachments/assets/8d46e907-e140-44cd-a76a-9aee3927f328" />
<img width="1127" height="671" alt="16" src="https://github.com/user-attachments/assets/f0b7681c-5aa6-4291-9286-8f6cbeb2575c" />
<img width="1126" height="615" alt="17" src="https://github.com/user-attachments/assets/89fbdda4-e636-4e20-ba9a-7c6d283a742b" />
<img width="1308" height="639" alt="18" src="https://github.com/user-attachments/assets/5bee913f-210b-4df3-acfd-e0f692df1d54" />
<img width="1347" height="693" alt="19" src="https://github.com/user-attachments/assets/a205fac8-c9cc-441c-a293-987582d9e520" />
<img width="1249" height="668" alt="20" src="https://github.com/user-attachments/assets/9769bb0a-0819-4b29-9d3a-0d550d999322" />

<img width="1081" height="672" alt="21" src="https://github.com/user-attachments/assets/a6ce0858-f8d1-4d42-a1b3-97c92c98d052" />
<img width="1293" height="516" alt="22" src="https://github.com/user-attachments/assets/98f4ac8a-8044-41c9-9d5b-45fc99811116" />

---

## 🧱 Step 6: Create Your First Jenkins Job

1. On the Jenkins dashboard, click **“New Item”**.

2. Enter a **name** for your job (e.g., `1st-job`).

3. Choose **Freestyle project** → Click **OK**.

4. Under **General**, add a **Description** if desired.

5. Under **Build**, click **Add build step** → **Execute shell**.

6. Add a simple script:

   ```bash
   echo "welcome to jenkins lab" > jenkins.txt  
   ```
7. Click **Save**.

8. On the job page, click **Build Now**.

<img width="1127" height="604" alt="24" src="https://github.com/user-attachments/assets/8b3404b2-dc2b-4fd4-b2b1-46bbe54b1598" />
<img width="1324" height="652" alt="25" src="https://github.com/user-attachments/assets/220e19ee-3955-4e81-9152-5e69d3457ab2" />
<img width="925" height="393" alt="26" src="https://github.com/user-attachments/assets/54628122-bb0a-444c-a178-3fee25d97e51" />
<img width="757" height="641" alt="27" src="https://github.com/user-attachments/assets/17d34689-ec7d-493f-a649-1c8a9388da4c" />



---

## 🧩 Step 7: View Job Console Output

Select **Console Output** to view your job logs.

---
<img width="1185" height="388" alt="28" src="https://github.com/user-attachments/assets/22c7072f-d5e4-4cbd-8747-575e9f3fc556" />
<img width="1094" height="384" alt="29" src="https://github.com/user-attachments/assets/9b41d9d1-ed55-4f85-9f4c-3906c99081a2" />
<img width="759" height="140" alt="30" src="https://github.com/user-attachments/assets/d46d2d97-ba06-446e-aed4-fa469a00fbb6" />
<img width="1287" height="363" alt="31" src="https://github.com/user-attachments/assets/d949b785-9141-4b85-8709-173da4aaf3a0" />



