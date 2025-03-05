![osTicket Screenshot](https://i.imgur.com/HyxCUMR.png)


# Installing osTicket on an MS Azure Virtual Machine

Set up your virtual machine. This part is not fully covered in this walk-through. The primary goal is to walk you through the initial installation of osTicket's Support Ticket System



First Create an Azure Virtual Machine
![VIrtual Machione Screenshot](https://imgur.com/zLv3Qh9.png)
Virtual Machine:

Windows 10 Pro, version 22H2, x64 Gen2 2-4 vCPUs

This guide provides a step-by-step tutorial on how to install **osTicket** on an **Azure Virtual Machine (VM)** running **Windows Server**. The setup includes configuring IIS (Internet Information Services), MySQL, and PHP.

## Prerequisites
- An **Azure account**
- A **Windows Server** Virtual Machine created in Azure
- Remote Desktop access to your VM

## 1. Set Up the Virtual Machine
1. Log in to **Azure Portal**.
2. Navigate to **Virtual Machines** > **Create a new VM**.
3. Choose an appropriate **Windows Server** image (e.g., Windows Server 2022).
4. Configure the VM settings:
   - **Size**: Choose at least **2 vCPUs and 4GB RAM**.
   - **Public IP**: Ensure it’s enabled.
   - **Allow ports**: Select **HTTP (80), HTTPS (443), and RDP (3389)**.
5. Click **Review + Create**, then **Create**.
6. Once deployed, use **Remote Desktop (RDP)** to connect to the VM.

## 2. Install IIS and PHP
### Install IIS
1. Open **Server Manager**.
2. Click **Manage** > **Add Roles and Features**.
3. Select **Role-based or feature-based installation** > Click **Next**.
4. Choose your **server**, then click **Next**.
5. Under **Server Roles**, check **Web Server (IIS)**.
6. Click **Next** until you reach **Install**, then click **Install**.
7. Restart the server after installation.

### Install PHP
1. Download the latest **PHP for Windows** from [https://windows.php.net/download/](https://windows.php.net/download/).
2. Extract PHP to `C:\php`.
3. Rename `php.ini-development` to `php.ini`.
4. Open **php.ini** and enable required extensions:
   ```ini
   extension=mbstring
   extension=mysqli
   extension=gd
   ```
5. Add `C:\php` to the **System Environment Variables**:
   - Right-click **This PC** > **Properties**.
   - Go to **Advanced system settings** > **Environment Variables**.
   - Under **System Variables**, find `Path` and click **Edit**.
   - Click **New** and enter `C:\php`.
   - Click **OK** and restart the VM.

## 3. Install MySQL
1. Download MySQL Community Edition from [https://dev.mysql.com/downloads/](https://dev.mysql.com/downloads/).
2. Run the installer and select **Custom Installation**.
3. Choose **MySQL Server** and **MySQL Workbench**.
4. Set the **root password** and create a user for osTicket:
   ```sql
   CREATE DATABASE osticket;
   CREATE USER 'osticket_user'@'localhost' IDENTIFIED BY 'StrongPassword';
   GRANT ALL PRIVILEGES ON osticket.* TO 'osticket_user'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ```

## 4. Download and Configure osTicket
1. Download osTicket from [https://osticket.com/download/](https://osticket.com/download/).
2. Extract osTicket to `C:\inetpub\wwwroot\osticket`.
3. Rename `ost-sampleconfig.php` to `ost-config.php`.
4. Set **file permissions**:
   - Right-click `ost-config.php` > **Properties** > **Security**.
   - Give `IUSR` and `IIS_IUSRS` **Full Control**.

## 5. Configure IIS for osTicket
1. Open **IIS Manager**.
2. Navigate to **Sites** > **Default Web Site**.
3. Right-click and select **Add Application**:
   - **Alias**: `osticket`
   - **Physical path**: `C:\inetpub\wwwroot\osticket`
4. Click **OK**.
5. Under **Default Document**, add `index.php` at the top.
6. Restart IIS:
   ```powershell
   iisreset
   ```

## 6. Install osTicket via Web Interface
1. Open a browser and go to:
   ```
   http://<your-server-ip>/osticket
   ```
2. Follow the installation wizard and enter MySQL details:
   - **Database Name**: `osticket`
   - **Username**: `osticket_user`
   - **Password**: `StrongPassword`
3. Click **Install Now**.

## 7. Post-Installation Steps
- **Remove the setup directory**:
  ```powershell
  Remove-Item -Recurse -Force C:\inetpub\wwwroot\osticket\setup
  ```
- **Set `ost-config.php` to read-only**.
- **Access the osTicket Admin Panel**:
  ```
  http://<your-server-ip>/osticket/scp
  ```
  - **Username**: `admin`
  - **Password**: `your chosen password during setup`

## Conclusion
You have successfully installed **osTicket** on an Azure Virtual Machine. Now, you can configure departments, email piping, and ticket management settings as needed.
