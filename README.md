# Create-OpenVPN-server-on-Pfsense

## Setup PROCEDURE

1. **As with any other system, before you make major changes, BACKUP YOUR SYSTEM.**  
   ![Backup System](https://i.ibb.co/Y7v1v16Y/Screenshot-115.png)

2. **Go to System → Certificates.**  
   Add a new Certificate Authority.  
   Set *Descriptive Name* and *Common Name* to your liking, then click **Save**.  
   ![Add Certificate Authority 1](https://i.ibb.co/MyDgcsJR/Screenshot-97.png)  
   ![Add Certificate Authority 2](https://i.ibb.co/hF01q4kK/Screenshot-99.png)  
   ![Add Certificate Authority 3](https://i.ibb.co/kW4dSgm/Screenshot-100.png)

3. **Click the Certificates tab** to create a new certificate for the CA you just created.  
   Under *Certificate Attributes → Certificate Type*, select **Server Certificate**.  
   Your CA cert is now created.  
   ![Create Server Certificate 1](https://i.ibb.co/YBPKxCW2/Screenshot-103.png)  
   ![Create Server Certificate 2](https://i.ibb.co/YBPKxCW2/Screenshot-103.png)  
   ![Create Server Certificate 3](https://i.ibb.co/vxN3WJcc/Screenshot-105.png)

4. **Go to System → User Manager → Add.**  
   This creates a new firewall user.  
   Enter a preferred username and password.  
   Under the *Certificate* property, check the box to create a user certificate.  
   ![Add Firewall User 1](https://i.ibb.co/ZRYSv42r/Screenshot-106.png)  
   ![Add Firewall User 2](https://i.ibb.co/5hVxxnrc/Screenshot-107.png)

5. **Set a descriptive name for the user certificate**, and set the CA to the one created in Step 2.  
   Save and return to *System → Certificates* to confirm your user cert has been created.  
   ![User Certificate 1](https://i.ibb.co/HfV89db6/Screenshot-108.png)  
   ![User Certificate 2](https://i.ibb.co/fRcXkpr/Screenshot-109.png)

6. **Go to VPN → OpenVPN → Wizards** to launch the setup wizard.  
   ![OpenVPN Wizard 1](https://i.ibb.co/LDfbHvYL/Screenshot-110.png)  
   ![OpenVPN Wizard 2](https://i.ibb.co/39VLmkW1/Screenshot-111.png)  
   ![OpenVPN Wizard 3](https://i.ibb.co/YB7KTLH0/Screenshot-112.png)  
   ![OpenVPN Wizard 4](https://i.ibb.co/bjhdyX58/Screenshot-113.png)

7. **Leave your port as 1194**, the OpenVPN default.  
   If you already have a working OpenVPN server, set another port (e.g., 1195) to avoid conflict.  
   ![Port Configuration](https://i.ibb.co/VYLwCkZ8/Screenshot-114.png)

8. **In Tunnel Settings**, set the *IPv4 local network* to match your pfSense LAN interface.  
   For the tunnel network, choose a random private subnet.  
   Finish the setup to complete the configuration.  
   ![Tunnel Settings 1](https://i.ibb.co/xqtBScSs/Screenshot-117.png)  
   ![Tunnel Settings 2](https://i.ibb.co/tptYHQ5X/Screenshot-118.png)  
   ![Tunnel Settings 3](https://i.ibb.co/hF7tm616/Screenshot-119.png)

9. **Verify your OpenVPN Server.**  
   Go to *VPN → OpenVPN → Servers*.  
   Click the pencil icon to edit and ensure both the **Peer Certificate Authority** and **Server Certificate** match the ones you created.  
   ![Verify OpenVPN Server](https://i.ibb.co/RTW8ynQQ/Screenshot-123.png)

10. **Install the OpenVPN Client Export Package.**  
    Go to *System → Package Manager → Available Packages*.  
    Search for and install the **OpenVPN Client Export** package.  
    Wait for installation to complete.  
    ![Package Manager 1](https://i.ibb.co/hF7tm616/Screenshot-119.png)  
    ![Package Manager 2](https://i.ibb.co/FkWxHcQ2/Screenshot-121.png)

11. **Go to VPN → OpenVPN → Client Export.**  
    Your remote access server should be listening on port 1194 if it’s the only one created.  
    Scroll to the *OpenVPN Clients* section — your user should appear there.  
    Download **Most Clients**.  
    ![Client Export 1](https://i.ibb.co/mr6PnyKS/Screenshot-124.png)  
    ![Client Export 2](https://i.ibb.co/Q7DmGWCJ/Screenshot-125.png)

12. **Import the Configuration into your OpenVPN Client.**  
    Enter your username and password.  
    Check “Save Password” to automatically authenticate into the VPN profile.  
    Click **Connect** to establish the VPN session.  
    ![Client Config 1](https://i.ibb.co/Q7DmGWCJ/Screenshot-125.png)  
    ![Client Config 2](https://i.ibb.co/mCvFqPwn/Screenshot-128.png)  
    ![Client Config 3](https://i.ibb.co/d49nr7jD/Screenshot-129.png)  
    ![Client Config 4](https://i.ibb.co/WvZJrZMm/Screenshot-131.png)

