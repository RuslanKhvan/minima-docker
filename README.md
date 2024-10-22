# minima-docker

#### **Prerequisites:**

- A VPS running **Ubuntu 18.04** or later (Debian-based OS is recommended).
- Root or sudo access to install required packages.
- Basic knowledge of Linux command-line operations.

---

### **Step 1: Update Your System**

Start by updating your system packages to the latest versions.

Open your terminal and run:

```bash
sudo apt-get update && sudo apt-get upgrade -y
```

This will ensure your system is up-to-date.

---

### **Step 2: Install Required Dependencies**

Minima requires Java 11 or higher to run. You can install OpenJDK 11 by running the following command:

```bash
sudo apt-get install openjdk-11-jdk -y
```

You can verify the installation by checking the version of Java installed:

```bash
java -version
```

Make sure that the output shows Java 11 or newer.

---

### **Step 3: Download and Install the Minima Node**

1. **Create a directory for Minima:**

   First, create a directory where the Minima files will be stored:

   ```bash
   mkdir ~/minima
   cd ~/minima
   ```

2. **Download the Minima installation script:**

   Use `wget` to download the installation script:

   ```bash
   wget https://github.com/minima-global/Minima/raw/master/scripts/minima_setup.sh
   ```

3. **Make the script executable:**

   Change the permissions of the script to make it executable:

   ```bash
   chmod +x minima_setup.sh
   ```

---

### **Step 4: Configure the Minima Node**

Now, you need to configure your Minima node before running the script.

1. **Run the installation script:**

   Execute the script with the following command:

   ```bash
   sudo ./minima_setup.sh -r 9001
   ```

   In this example, the node will run on port `9001`. You can change this to any available port, but ensure that it is open on your VPS firewall.

2. **Open the required port:**

   You need to open the port you specified (`9001` in this case) to allow the Minima node to communicate. Use the following command to open the port:

   ```bash
   sudo ufw allow 9001
   ```

---

### **Step 5: Check Minima Node Status**

After the installation is complete, the Minima node will start automatically.

You can check the status of the node using:

```bash
sudo systemctl status minima
```

If everything is working correctly, you should see an output indicating that the Minima node is active and running.

---

### **Step 6: Verify Your Node is Running**

You can use the following command to view the log output of the Minima node:

```bash
tail -f ~/minima/minimalog.txt
```

This will display the log file in real time, showing any activity of your Minima node.

---

### **Step 7: Set Up Auto-Restart on Reboot (Optional)**

To ensure that your Minima node starts automatically whenever your VPS reboots, enable the service:

```bash
sudo systemctl enable minima
```

---

### **Step 8: Interact with the Node (Optional)**

To interact with the node and get basic information, use the `curl` command with your node’s IP address or domain name:

```bash
curl http://127.0.0.1:9001/invocation?function=info
```

This will return information about your node’s status and performance.

---

### **Step 9: Upgrade or Uninstall (Optional)**

- **To upgrade the node** when a new version is released, run the setup script again:

  ```bash
  sudo ./minima_setup.sh -r 9001
  ```

- **To uninstall the Minima node**, use the command:

  ```bash
  sudo ./minima_setup.sh -u
  ```
