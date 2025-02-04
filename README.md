# rpi
raspberry pi stuff

## Installation

### Hardware requirements

![picture 0](images/8602cc0f9d2013edb9d7422bb16c8bdf39555a97a3682dca80b147528a4e374c.png)  

Go to 

https://www.raspberrypi.com/software/

and install raspberry image app

![picture 2](images/178cbb6a6a05464c279627a8f4bedf8bf78605612518341b028d44975d52273d.png)  

Insert SD card

![picture 8](images/7c157f75b1179b90aee002c38dfb68be1b814db1b218f887c97ab7c679435a98.png)  

Start the app

![picture 1](images/4e1d8188d06d43aaa0181c37f7369697fc725889bb3f2efa76735a9dd0d86ed8.png)  

Select your device

![picture 3](images/11026dfcfff45812593adb64b5111d372eeac3cf50cfa29d9c2cfc01ec9d1f14.png)  

continue

![picture 4](images/0d649440687c76e4e46ccc6531c7e84d2a060e42c5660ee780ed9118e30badb2.png)  

> **Note:** If you have a keyboard, a mouse and a monitor and can connect them, the following settings can also be carried out later directly on the monitor.

Settings:

![picture 5](images/b1390dcf3b11ec061eb71f5617467c8e991e5da771207f55c4af19a983abed5e.png)  

![picture 6](images/2f6abbdcb9a37c3175e4e74124e42adacbe759d0cd151c629a6a8f9e081d34a9.png)  

# How to Create an SSH Key on macOS and Windows  

Secure Shell (SSH) keys provide a secure way to authenticate with remote servers without using passwords. Here’s how to generate an SSH key on **macOS** and **Windows**.

---

## **🔑 Creating an SSH Key on macOS**  
1. **Open Terminal** (`Cmd + Space`, type "Terminal", and press Enter).  
2. Run the following command to generate an SSH key:  
   ```sh
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   - `-t rsa` → Uses the RSA algorithm.  
   - `-b 4096` → Creates a strong 4096-bit key.  
   - `-C "your_email@example.com"` → Adds an identifier (your email).  

3. When prompted, press **Enter** to save the key in the default location (`~/.ssh/id_rsa`).  
4. Set a **passphrase** (optional but recommended).  
5. Copy the public key to your clipboard:  
   ```sh
   cat ~/.ssh/id_rsa.pub | pbcopy
   ```
6. Add the key to an SSH agent:  
   ```sh
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
7. Your SSH key is now ready to use!

---

## **🖥️ Creating an SSH Key on Windows**  

### **Option 1: Using PowerShell (Recommended)**
1. Open **PowerShell** (Win + X → Windows Terminal / PowerShell).  
2. Run the SSH keygen command:  
   ```powershell
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
3. Press **Enter** to save in the default location (`C:\Users\YourUser\.ssh\id_rsa`).  
4. Set a **passphrase** if desired.  
5. Copy the public key:  
   ```powershell
   Get-Content $env:USERPROFILE\.ssh\id_rsa.pub | Set-Clipboard
   ```
6. Start the SSH agent and add the key:  
   ```powershell
   Start-Service ssh-agent
   ssh-add $env:USERPROFILE\.ssh\id_rsa
   ```

### **Option 2: Using PuTTY (For Older Windows Versions)**
1. Download **PuTTYgen** from [PuTTY's website](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).  
2. Open PuTTYgen → Click **Generate** → Move your mouse randomly to create entropy.  
3. Save the **private key** (`.ppk`) and **public key**.  
4. Add the key to SSH authentication.

---

## **🔗 Using the SSH Key**  
Once your key is generated, add the **public key** (`id_rsa.pub`) to your remote server or services like GitHub/GitLab by pasting it into the SSH settings.

Now, you can connect securely without using passwords! 🚀


![picture 7](images/78a8e1453d4fc65ee5dd5aaef8d83ca279449f8f987f8b1c7dcf19d5b307a99e.png)  

Insert card to raspberry pi:

![picture 9](images/bc521892cd6bf9ae368bc0d3ef2550b88b5ac33507c669ae45a08be96e7437a5.png)  

Connect to power supply:

![picture 10](images/491a8060315f7c22de1c5492d1f77a08d12b3c899edde56b15a2658f769b19ad.png)  

connect to your raspberry via ssh:

ssh pi@bix-rpi-0.local

> *Note:* This will only work if your router could resolve the name via DNS otherwise start with the ip address.

You can add the following entry to your ~/.ssh/config:

```config
Host rpi0
Hostname bix-rpi-0.local # or the ip address here
StrictHostKeyChecking no
User pi
IdentityFile ~/.ssh/id_rsa
```

# K3s

https://medium.com/@stevenhoang/step-by-step-guide-installing-k3s-on-a-raspberry-pi-4-cluster-8c12243800b9

