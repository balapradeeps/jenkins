# Install Jenkins on Ubuntu 22.04
### July 2024 created this doc

## Step 1: Install Java

Jenkins is a Java-based application, so you need to install the Java Development Kit (JDK). OpenJDK 17 is a suitable version. Open a terminal and run:

```bash
sudo apt update
sudo apt install openjdk-17-jre -y
```

Verify the Java installation:

```bash
java -version
```

## Step 2: Add the Jenkins Repository

Since Jenkins is not included in the default Ubuntu repositories, you need to add its official repository. Execute the following commands:

```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update

```

Update the package index to recognize the new repository:

```bash
sudo apt update
```

## Step 3: Install Jenkins

Now, install Jenkins using the following command:

```bash
sudo apt install jenkins -y
```

## Step 4: Start and Enable Jenkins Service

After installation, start the Jenkins service and enable it to start on boot:

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Check the status of the Jenkins service to ensure it's running:

```bash
sudo systemctl status jenkins
```

## Step 5: Configure Firewall

If you have a firewall enabled, allow traffic on Jenkins' default port (8080):

```bash
sudo ufw allow 8080/tcp
sudo ufw reload
```

## Step 6: Access Jenkins Setup Wizard

Open your web browser and navigate to:

```
http://your_server_ip_or_domain:8080
```

To unlock Jenkins, retrieve the initial admin password with the following command:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password and paste it into the "Administrator password" field in the web interface. Click "Continue" and follow the prompts to install suggested plugins and set up your admin user.



# For security reasons, if you want to change the default Jenkins port, you can use this after installation:

1. **Open Jenkins Configuration File**:

   Open the Jenkins default configuration file using a text editor. The file is usually located at `/etc/default/jenkins` on Debian-based systems.

   ```bash
   sudo nano /etc/default/jenkins
   ```

2. **Change the HTTP Port**:

   Find the line that specifies the `HTTP_PORT` and change its value from 8080 to `your port`

   ```plaintext
   # previous line
   HTTP_PORT=8080
   # new line
   HTTP_PORT=8888
   ```

3. **Save and Exit**:

   Save the file and exit the text editor. In `nano`, you can do this by pressing `Ctrl+X`, then `Y` to confirm the changes, and `Enter` to exit.

4. **Reload Systemd Configuration**:

   Reload the systemd manager configuration to pick up the changes.

   ```bash
   sudo systemctl daemon-reload
   ```

5. **Restart Jenkins Service**:

   Restart the Jenkins service to apply the new port configuration.

   ```bash
   sudo systemctl restart jenkins
   ```

6. **Verify Jenkins is Running on the New Port**:

   Check the status of Jenkins to ensure it is running on the new port.

   ```bash
   sudo systemctl status jenkins
   ```

   You can also open a web browser and navigate to `http://your_server_ip:8888` to access Jenkins on the new port.

### Additional Notes:

- Ensure that the new port (8888) is open in your firewall or security group settings if you are running Jenkins on a cloud server.
- If you encounter any issues, check the Jenkins logs for more details.

   ```bash
   sudo tail -f /var/log/jenkins/jenkins.log
   ```
