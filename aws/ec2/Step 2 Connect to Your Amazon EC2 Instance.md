# Step 2: Connect to Your Amazon EC2 Instance

Now that you have launched your EC2 instance, you can connect to it and use it the way that you'd use a computer sitting in front of you.

This topic describes the following ways of connecting to a Linux instance:

- [Connect from Windows using PuTTY](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html#putty)
- [Connect from Mac or Linux Using an SSH Client](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html#sshclient)
- [Connect Using Your Browser](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html#browser)

## Connect from Windows using PuTTY

PuTTY uses .ppk files instead of .pem files. If you haven't already generated a .ppk file, do so now. For more information, see [To prepare to connect to a Linux instance from Windows using PuTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html#prepare-for-putty).

**To connect using PuTTY**

1. On the **Start** menu, choose **All Programs**, **PuTTY**, **PuTTY**.

2. In the **Category** pane, choose **Session** and complete the following fields:

   - For **Host Name**, enter `ec2-user@public_dns_name`.

     **Note**

     You can get the public DNS for your instance using the Amazon EC2 console. (If the **Public DNS** column is hidden, choose the **Show/Hide** icon.)

   - For **Connection type**, choose **SSH**.

   - For **Port**, ensure that the value is **22**.

   ![             PuTTY configuration dialog box           ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-putty-1.png)

3. In the **Category** pane, choose **Connection**, **SSH**, and **Auth**. Complete the following:

   - Choose **Browse**, select the .ppk file that you generated for your key pair, and then choose **Open**.
   - Choose **Open** to start the PuTTY session.

   ![             Opening a PuTTY session           ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-putty-2.png)

4. If this is the first time you have connected to this instance, PuTTY displays a security alert dialog box that asks whether you trust the host you are connecting to. Choose **Yes**. A window opens and you are connected to your instance.

## Connect from Mac or Linux Using an SSH Client

Your Mac or Linux computer most likely includes an SSH client by default. You can check for an SSH client by typing `ssh` at the command line. If your computer doesn't recognize the command, the OpenSSH project provides a free implementation of the full suite of SSH tools. For more information, go to [http://www.openssh.org](http://www.openssh.org/).

**To connect using SSH**

1. Open your command line shell and change the directory to the location of the private key file that you created when you launched the instance.

   Use the **chmod** command to make sure your private key file isn't publicly viewable. For example, if the name of your private key file is my-key-pair.pem, use the following command:

   **chmod 400 my-key-pair.pem**

2. Use the following SSH command to connect to the instance:

   **ssh -i /path/my-key-pair.pem ec2-user@public_dns_name**

   **Note**

   For this quick start, you used the Amazon Linux AMI for your instance, so the user name is ec2-user.

   **Note**

   You can get the public DNS for your instance using the Amazon EC2 console. (If the **Public DNS** column is hidden, choose the **Show/Hide** icon.)

## Connect Using Your Browser

Using a browser is the fastest way to connect to your instance. It is recommended you use Firefox or Safari to complete the procedure below since Java is disabled in Chrome. If you don't have Java already, you can contact your system administrator to get it installed, or follow the steps outlined in the following pages: [Install Java](http://java.com/en/download/help/index_installing.xml) and [Enable Java](http://java.com/en/download/help/enable_browser.xml) in your web browser.

**To connect using a browser**

1. On the Amazon EC2 console, in the navigation pane, choose **Instances**.

2. Select the instance that you launched and choose **Connect**.

   ![             List of instances available for connection           ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-browser-1.png)

3. Choose **A Java SSH client directly from my browser (Java required)**.

4. Amazon EC2 automatically detects the public DNS name of your instance and populates **Public DNS** for you. It also detects the key pair that you specified when you launched the instance. Complete the following, and then choose **Launch SSH Client**.

   - For **User name**, enter `ec2-user`.
   - For **Private key path**, enter the fully qualified path to your private key (.pem) file, including the key pair name, for example, `C:\KeyPairs\my-key-pair.pem`.
   - (Optional) Choose **Store in browser cache** to store the location of the private key in your browser cache. This enables Amazon EC2 to detect the location of the private key in subsequent browser sessions, until you clear your browser's cache.

   ![             Connect To Your Instance dialog box           ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-browser-2.png)

5. If necessary, choose **Yes** to trust the certificate and **Run** to run the MindTerm client.

6. If this is your first time running MindTerm, a series of dialog boxes asks you to accept the license agreement, to confirm setup for your home directory, and to confirm setup of the known hosts directory.

7. A dialog box prompts you to add the host to your set of known hosts. If you do not want to store the host key information on your local computer, choose **No**.

8. A window opens and you are connected to your instance.

   