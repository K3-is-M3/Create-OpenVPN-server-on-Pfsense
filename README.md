# Create-OpenVPN-server-on-Pfsense

## Setup Procedure

1. **Backup your system**  
   As with any other system, before making major configuration changes, always back up your system.  
   ![Backup System](https://ibb.co/svLNLNhk)

---

2. **Create a Certificate Authority (CA)**  
   Go to **System → Certificates**.  
   Click **Add** to create a new Certificate Authority.  
   Set the *Descriptive Name* and *Common Name* to your preference, then click **Save**.  
   ![Add CA 1](https://ibb.co/6cRyHmq4)  
   ![Add CA 2](https://ibb.co/HTZpJb0r)  
   ![Add CA 3](https://ibb.co/S9tL3Xf)

---

3. **Create a Server Certificate**  
   Click the **Certificates** tab and create a new certificate for the CA you just made.  
   Under **Certificate Attributes → Certificate Type**, select **Server Certificate**.  
   Your CA certificate is now created.  
   ![Server Cert 1](https://ibb.co/ZzGw0jJd)  
   ![Server Cert 2](https://ibb.co/DPc7dxHz)  
   ![Server Cert 3](https://ibb.co/PZ2cy5rr)

---

4. **Add a New Firewall User**  
   Navigate to **System → User Manager → Add** to create a new firewall user.  
   Enter your preferred **username** and **password**.  
   Under the **Certificate** section, check the box to generate a user certificate.  
   ![Add User 1](https://ibb.co/8ndbGvYw)  
   ![Add User 2](https://ibb.co/JjPFFyvk)

---

5. **Create a User Certificate**  
   Provide a **descriptive name** for the user certificate.  
   Set the **CA** to the one you created in Step 2.  
   Click **Save**, then return to **System → Certificates** to confirm that your user certificate has been created.  
   ![User Cert 1](https://ibb.co/ksxCP1wj)  
   ![User Cert 2](https://ibb.co/kndG48q)

---

6. **Launch the OpenVPN Wizard**  
   Go to **VPN → OpenVPN**, then click on the **Wizards** tab to launch the setup wizard.  
   ![Wizard 1](https://ibb.co/gbCHh6m5)  
   ![Wizard 2](https://ibb.co/Xr6vxVpX)  
   ![Wizard 3](https://ibb.co/WvWdp2mV)  
   ![Wizard 4](https://ibb.co/p6DXsdj9)

---

7. **Set the VPN Port**  
   Leave the default port as **1194**, which is the standard OpenVPN port.  
   *(In this example, port 1195 is used to avoid conflict with another existing OpenVPN server.)*  
   ![Port Config](https://ibb.co/7tSkp05F)

---

8. **Configure Tunnel Settings**  
   Under **Tunnel Settings**, set the **IPv4 Local Network** to match your LAN interface configuration.  
   For the **Tunnel Network**, select a random private subnet.  
   Click **Finish** to complete the setup.  
   ![Tunnel 1](https://ibb.co/HTfbDMD2)  
   ![Tunnel 2](https://ibb.co/HTsGKBQd)  
   ![Tunnel 3](https://ibb.co/9H8CrD3D)

---

9. **Install OpenVPN Client Export Package**  
   Go to **System → Package Manager**.  
   Under the **Available Packages** tab, search for `openvpn-client-export` and install it.  
   Wait for the installation to complete.  
   ![Package 1](https://ibb.co/R4G7WkYL)  
   ![Package 2](https://ibb.co/vCBwXfNp)

---

10. **Export OpenVPN Client Configuration**  
    Go to **VPN → OpenVPN → Client Export**.  
    Your Remote Access Server should be listed, typically listening on port **1194**.  
    Scroll to the **OpenVPN Clients** section and locate your user.  
    Download the **Most Clients** configuration package.  
    ![Client Export 1](https://ibb.co/35BPxFbk)  
    ![Client Export 2](https://ibb.co/9mZYjxVp)

---

11. **Import Configuration into OpenVPN Client**  
    Import the downloaded configuration file into your OpenVPN client.  
    Enter your **username** and **password**, then check the **Save Password** box for automatic authentication.  
    Click **Connect** to establish your VPN connection.  
    ![Client Config 1](https://ibb.co/RGyB5237)  
    ![Client Config 2](https://ibb.co/pvWrzk8H)  
    ![Client Config 3](https://ibb.co/ch5z1xkQ)

---

✅ **Your OpenVPN server setup on pfSense is now complete!**  
You should now be able to connect securely using your generated client profile.
