# 🧱 Create an OpenVPN Server on pfSense

## ⚙️ Setup Procedure

---

### 🔹 Step 1: Backup Your System  
Before making any major configuration changes, **always create a backup** of your current pfSense setup.

![Backup System](https://i.ibb.co/Y7v1v16Y/Screenshot-115.png)

---

### 🔹 Step 2: Create a Certificate Authority (CA)  
Navigate to **System → Certificates** and click **Add** to create a new Certificate Authority.  

- Set a **Descriptive Name** and **Common Name** to your liking.  
- Click **Save** to complete this step.

![Add Certificate Authority 1](https://i.ibb.co/MyDgcsJR/Screenshot-97.png)  
![Add Certificate Authority 2](https://i.ibb.co/hF01q4kK/Screenshot-99.png)  
![Add Certificate Authority 3](https://i.ibb.co/kW4dSgm/Screenshot-100.png)

---

### 🔹 Step 3: Create a Server Certificate  
Go to the **Certificates** tab to create a certificate for your new CA.

- Under **Certificate Attributes → Certificate Type**, select **Server Certificate**.  
- Click **Save**.  
Your CA certificate is now created successfully.

![Create Server Certificate 1](https://i.ibb.co/YBPKxCW2/Screenshot-103.png)  
![Create Server Certificate 2](https://i.ibb.co/YBPKxCW2/Screenshot-103.png)  
![Create Server Certificate 3](https://i.ibb.co/vxN3WJcc/Screenshot-105.png)

---

### 🔹 Step 4: Create a New Firewall User  
Navigate to **System → User Manager → Add** to create a new pfSense user.  

- Enter a **Username** and **Password** of your choice.  
- Check the box under **Certificate** to generate a user certificate for this account.

![Add Firewall User 1](https://i.ibb.co/ZRYSv42r/Screenshot-106.png)  
![Add Firewall User 2](https://i.ibb.co/5hVxxnrc/Screenshot-107.png)

---

### 🔹 Step 5: Generate a User Certificate  
Assign a **Descriptive Name** for the user certificate.  
Select the **CA** you created in Step 2, then click **Save**.  

Return to **System → Certificates** to confirm that the user certificate has been created.

![User Certificate 1](https://i.ibb.co/HfV89db6/Screenshot-108.png)  
![User Certificate 2](https://i.ibb.co/fRcXkpr/Screenshot-109.png)

---

### 🔹 Step 6: Launch the OpenVPN Wizard  
Go to **VPN → OpenVPN → Wizards** to begin the guided setup process.

![OpenVPN Wizard 1](https://i.ibb.co/LDfbHvYL/Screenshot-110.png)  
![OpenVPN Wizard 2](https://i.ibb.co/39VLmkW1/Screenshot-111.png)  
![OpenVPN Wizard 3](https://i.ibb.co/YB7KTLH0/Screenshot-112.png)  
![OpenVPN Wizard 4](https://i.ibb.co/bjhdyX58/Screenshot-113.png)

---

### 🔹 Step 7: Configure OpenVPN Port and Protocol  
By default, OpenVPN listens on **port 1194**.  
If you already have another OpenVPN instance, you may set a different port (e.g., **1195**) to avoid conflict.

> **Note:** For production environments, **UDP** is preferred over **TCP**.  
> UDP offers faster performance and is better suited for real-time network traffic.

![Port Configuration](https://i.ibb.co/VYLwCkZ8/Screenshot-114.png)

---

### 🔹 Step 8: Configure Tunnel Settings  
Under **Tunnel Settings**:

- I Set the **IPv4 Local Network** to match my pfSense LAN interface.  
- I also assigned a random **Private Subnet** for the tunnel network.  
- Review all other options and click **Finish** to complete the wizard.

![Tunnel Settings 1](https://i.ibb.co/xqtBScSs/Screenshot-117.png)  
![Tunnel Settings 2](https://i.ibb.co/tptYHQ5X/Screenshot-118.png)  
![Tunnel Settings 3](https://i.ibb.co/hF7tm616/Screenshot-119.png)

---

### 🔹 Step 9: Verify OpenVPN Server Configuration  
Go to **VPN → OpenVPN → Servers**.  

Click the **Edit (pencil)** icon and confirm that both the **Peer Certificate Authority** and **Server Certificate** match the ones you created earlier.

![Verify OpenVPN Server](https://i.ibb.co/RTW8ynQQ/Screenshot-123.png)

---

### 🔹 Step 10: Install the OpenVPN Client Export Package  
Go to **System → Package Manager → Available Packages**.  

- Search for **OpenVPN Client Export**.  
- Click **Install**, then wait for the installation to complete.

![Package Manager 1](https://i.ibb.co/hF7tm616/Screenshot-119.png)  
![Package Manager 2](https://i.ibb.co/FkWxHcQ2/Screenshot-121.png)

---

### 🔹 Step 11: Export the Client Configuration  
Navigate to **VPN → OpenVPN → Client Export**.

- Ensure your **Remote Access Server** is listening on the correct port (default: 1194).  
- Scroll down to the **OpenVPN Clients** section.  
- Locate your user and download **Most Clients** configuration package.

![Client Export 1](https://i.ibb.co/mr6PnyKS/Screenshot-124.png)  
![Client Export 2](https://i.ibb.co/Q7DmGWCJ/Screenshot-125.png)

---

### 🔹 Step 12: Import and Connect the VPN Client  
Import the downloaded configuration file into your OpenVPN client.  

- Enter your **Username** and **Password**.  
- Optionally check **Save Password** to enable automatic authentication.  
- Click **Connect** to establish your VPN session.

![Client Config 1](https://i.ibb.co/Q7DmGWCJ/Screenshot-125.png)  
![Client Config 2](https://i.ibb.co/mCvFqPwn/Screenshot-128.png)  
![Client Config 3](https://i.ibb.co/d49nr7jD/Screenshot-129.png)  
![Client Config 4](https://i.ibb.co/WvZJrZMm/Screenshot-131.png)

---

## ✅ Conclusion  
Your **OpenVPN Server** is now fully configured and ready to provide secure remote access through pfSense.  
Users can authenticate with their credentials, automatically establish encrypted tunnels, and access the internal network securely.

> **Note:** Your network environment may be setup differently and thus you need to review that first and understand how you have set it up.  


