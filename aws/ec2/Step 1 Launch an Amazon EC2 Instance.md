# Step 1: Launch an Amazon EC2 Instance

This topic describes the steps of launching a new Linux EC2 instance. To launch a Windows instance, see [Getting Started with Amazon EC2 Windows Instances](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2Win_GetStarted.html).

Because this guide is intended to help you launch your first instance quickly, it does not describe all the available configuration options for EC2 instances. For more information about advanced options, see [Launching an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html).

**Important**

This quick start guide uses a new version of the [AWS Management Console](https://console.aws.amazon.com/) that is currently in preview release and is subject to change.

**To launch an EC2 instance**

1. Sign in to the preview version of the [AWS Management Console](https://console.aws.amazon.com/).

2. Open the Amazon EC2 console by choosing **EC2** under **Compute**.

   If you are using the **Show All Services** view, your screen looks like this:

   ![           AWS services on the console         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/aws-console-vm.png)

   If you are using the **Show Categories** view, your screen looks like this with **Compute** expanded:

   ![           AWS services on the console         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/aws-console-vm-categorized.png)

3. From the Amazon EC2 dashboard, choose **Launch Instance**.

   ![           Amazon EC2 console dashboard         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-launch-instance.png)

4. The **Choose an Amazon Machine Image (AMI)** page displays a list of basic configurations called Amazon Machine Images (AMIs) that serve as templates for your instance. Select the HVM edition of the **Amazon Linux AMI**. Notice that this configuration is marked **Free tier eligible**.

   ![           List of available AMIs         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-linux-ami.png)

5. On the **Choose an Instance Type** page, choose **t.2micro** as the hardware configuration of your instance and **Review and Launch**.

   **Note**

   T2 instances, such as **t2.micro**, must be launched into a virtual private cloud (VPC). If you don't have a VPC, you can let the wizard create one for you. For more information, see step 6 in [Launching an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html).

   ![           List of available instance types         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-t2micro.png)

6. On the **Review Instance Launch** page, choose **Launch**.

   **Note**

   On the **Review Instance Launch** page, under **Security Groups**, you see that the wizard created and selected a security group for you. For the purposes of this quick start, no further action than what is described in step 6 above is necessary. For more information about how to create or configure a security group and define firewall rules for your instance, see step 9 in [Launching an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html).

   ![           Review your launch configuration         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-review-launch.png)

7. In the **Select an existing key pair or create a new key pair** dialog box, choose **Create a new key pair**, enter a name for the key pair, and then choose **Download Key Pair**. This is the only chance for you to save the private key file, so be sure to download it. Save the private key file in a safe place. You can use `C:\user\yourusername\.ssh\myfirstkey.pem` if you are on a Windows machine, and `~/.ssh/myfirstkey.pem` if you are on a Mac or Linux machine. You need to provide the name of your key pair when you launch an instance, and the corresponding private key each time you connect to the instance.

   **Note**

   A key pair enables you to connect to a Linux instance through SSH. If you launch your instance without a key pair, then you can't connect to it. We recommend against choosing the **Proceed without a key pair** option.

   When you are ready, select the acknowledgment check box, and then choose **Launch Instances**.

   ![           Select an existing key pair or create a new key               pair dialog box         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-new-key-pair.png)

8. A confirmation page lets you know that your instance is launching. Choose **View Instances** to close the confirmation page and return to the console.

On the **Instances** page, you can view the status of your instance. It takes a short time for an instance to launch. When you launch an instance, its initial state is pending. After the instance starts, its state changes to running, and it receives a public DNS name. (If the **Public DNS** column is hidden, choose the **Show/Hide** icon.)