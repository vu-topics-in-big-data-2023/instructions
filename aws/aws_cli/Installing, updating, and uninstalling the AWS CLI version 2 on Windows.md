# Installing, updating, and uninstalling the AWS CLI version 2 on Windows

Source: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html

This section describes how to install, update, and remove the AWS CLI version 2 on Windows.

**Important**

AWS CLI versions 1 and 2 use the same `aws` command name. If you have both versions installed, your computer uses the first one found in your search path. If you previously installed AWS CLI version 1, we recommend that you do one of the following to use AWS CLI version 2:

- **Recommended** – Uninstall AWS CLI version 1 and use only AWS CLI version 2. For uninstall instructions, determine the method you used to install AWS CLI version 1 and follow the appropriate uninstall instructions for your operating system in [Installing, updating, and uninstalling the AWS CLI version 1](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html)
- Use your operating system's ability to create a symbolic link (symlink) or alias with a different name for one of the two `aws` commands. For example, you can use a [symbolic link](https://www.linux.com/tutorials/understanding-linux-links/) or [alias](https://www.linux.com/tutorials/aliases-diy-shell-commands/) on Linux and macOS, or [`DOSKEY`](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/doskey) on Windows.

For information on breaking changes between version 1 and version 2, see [Breaking changes – Migrating from AWS CLI version 1 to version 2](https://docs.aws.amazon.com/cli/latest/userguide/cliv2-migration.html).

## Prerequisites

Before you can install or update the AWS CLI version 2 on Windows, be sure you have the following:

- A 64-bit version of Windows XP or later.
- Admin rights to install software

## Install or update the AWS CLI version 2 on Windows using the MSI installer

1. Download the AWS CLI MSI installer for Windows (64-bit):

   - **For the latest version of the AWS CLI:** https://awscli.amazonaws.com/AWSCLIV2.msi
   - **For a specific version of the AWS CLI:** Append a hyphen and the version number to the filename. For this example the filename for version `2.0.30` would be `AWSCLIV2-2.0.30.msi` resulting in the following link https://awscli.amazonaws.com/AWSCLIV2-2.0.30.msi. For a list of versions, see the [AWS CLI version 2 changelog](https://github.com/aws/aws-cli/blob/v2/CHANGELOG.rst) on *GitHub*.

   To update your current installation of AWS CLI version 2 on Windows, download a new installer each time you update to overwrite previous versions. AWS CLI is updated regularly. To see when the latest version was released, see the [AWS CLI version 2 changelog](https://github.com/aws/aws-cli/blob/v2/CHANGELOG.rst) on *GitHub*.

2. Run the downloaded MSI installer and follow the on-screen instructions. By default, the AWS CLI installs to `C:\Program Files\Amazon\AWSCLIV2`.

3. To confirm the installation, open the **Start** menu, search for `cmd` to open a command prompt window, and at the command prompt use the `aws --version` command.

   Don't include the prompt symbol (`C:\>`) when you type a command. These are included in program listings to differentiate commands that you type from output returned by the AWS CLI. The rest of this guide uses the generic prompt symbol (`$`), except in cases where a command is Windows-specific. For more information about how we format code examples, see [Using the AWS CLI examples](https://docs.aws.amazon.com/cli/latest/userguide/welcome-examples.html).

   ```powershell
   C:\> aws --version
   aws-cli/2.1.1 Python/3.7.4 Windows/10 botocore/2.0.0
   ```

   If Windows is unable to find the program, you might need to close and reopen the command prompt window to refresh the path, or [add the installation directory to your PATH](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#awscli-install-windows-path) environment variable manually.

## Uninstall the AWS CLI version 2 from Windows

1. Open **Programs and Features** by doing one of the following:

   - Open the **Control Panel**, and then choose **Programs and Features**.

   - Open a command prompt, and then enter the following command.

     ```powershell
     C:\> appwiz.cpl
     ```

2. Select the entry named **AWS Command Line Interface**, and then choose **Uninstall** to launch the uninstaller.

3. Confirm that you want to uninstall the AWS CLI.