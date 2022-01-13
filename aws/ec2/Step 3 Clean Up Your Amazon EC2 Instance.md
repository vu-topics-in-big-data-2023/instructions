# Step 3: Clean Up Your Amazon EC2 Instance

After you are finished with the instance that you created for this quick start, you can clean up by terminating the instance.

Terminating an instance effectively deletes it because you can't reconnect to an instance after you've terminated it. This differs from stopping the instance; when you stop an instance, it is shut down and you are not billed for hourly usage or data transfer (but you are billed for any Amazon EBS volume storage). Also, you can restart a stopped instance at any time. For more information about the differences between stopping and terminating an instance, see [Stopping Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html).

**To terminate an instance**

1. In the Amazon EC2 console, on the **Instances** page, locate your instance.

2. Open the context (right-click) menu for the instance and choose **Instance State**, **Terminate**.

   ![           Context menu for an instance         ](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/images/vm-terminate.png)

3. Choose **Yes, Terminate** when prompted for confirmation.

   Amazon EC2 shuts down and terminates your instance. After your instance is terminated, it remains visible on the console for a short while, and then the entry is deleted.

