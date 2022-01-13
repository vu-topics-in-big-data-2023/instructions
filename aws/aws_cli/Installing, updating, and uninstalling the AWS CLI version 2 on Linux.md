# Installing, updating, and uninstalling the AWS CLI version 2 on Linux

Source: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html

This section describes how to install, update, and remove the AWS CLI version 2 on Linux. The AWS CLI version 2 has no dependencies on other Python packages. It has a self-contained, embedded copy of Python included in the installer.

**Important**

AWS CLI versions 1 and 2 use the same `aws` command name. If you have both versions installed, your computer uses the first one found in your search path. If you previously installed AWS CLI version 1, we recommend that you do one of the following to use AWS CLI version 2:

- **Recommended** – Uninstall AWS CLI version 1 and use only AWS CLI version 2. For uninstall instructions, determine the method you used to install AWS CLI version 1 and follow the appropriate uninstall instructions for your operating system in [Installing, updating, and uninstalling the AWS CLI version 1](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html)
- Use your operating system's ability to create a symbolic link (symlink) or alias with a different name for one of the two `aws` commands. For example, you can use a [symbolic link](https://www.linux.com/tutorials/understanding-linux-links/) or [alias](https://www.linux.com/tutorials/aliases-diy-shell-commands/) on Linux and macOS, or [`DOSKEY`](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/doskey) on Windows.

For information on breaking changes between version 1 and version 2, see [Breaking changes – Migrating from AWS CLI version 1 to version 2](https://docs.aws.amazon.com/cli/latest/userguide/cliv2-migration.html).

## Prerequisites for Linux

- You must be able to extract or "unzip" the downloaded package. If your operating system doesn't have the built-in `unzip` command, use an equivalent.
- The AWS CLI version 2 uses `glibc`, `groff`, and `less`. These are included by default in most major distributions of Linux.
- We support the AWS CLI version 2 on 64-bit versions of recent distributions of CentOS, Fedora, Ubuntu, Amazon Linux 1, and Amazon Linux 2.
- We support the AWS CLI version 2 on Linux ARM.
- Because AWS doesn't maintain third-party repositories, we can’t guarantee that they contain the latest version of the AWS CLI.

## Install the AWS CLI version 2 on Linux x86(64-bit)

**For the latest version of the AWS CLI,** use the following command block:

```shell
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```

**For a specific version of the AWS CLI,** append a hyphen and the version number to the filename. For this example the filename for version `2.0.30` would be `awscli-exe-linux-x86_64-2.0.30.zip` resulting in the following command:

```shell
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.0.30.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```

For a list of versions, see the [AWS CLI version 2 changelog](https://github.com/aws/aws-cli/blob/v2/CHANGELOG.rst) on *GitHub*.

## Install the AWS CLI version 2 on Linux ARM

**For the latest version of the AWS CLI,** use the following command block:

```shell
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

**For a specific version of the AWS CLI,** append a hyphen and the version number to the filename. For this example the filename for version `2.0.30` would be `awscli-exe-linux-aarch64-2.0.30.zip` resulting in the following command:

```shell
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64-2.0.30.zip" -o "awscliv2.zip"
```

For a list of versions, see the [AWS CLI version 2 changelog](https://github.com/aws/aws-cli/blob/v2/CHANGELOG.rst) on *GitHub*.

## Confirm the installation.

```shell
$ aws --version
aws-cli/2.1.1 Python/3.7.4 Linux/4.14.133-113.105.amzn2.x86_64 botocore/2.0.0
```

## Uninstall the AWS CLI version 2 on Linux

To uninstall the AWS CLI version 2, run the following commands.

1. Locate the symlink and install paths.

   - Use the `which` command to find the symlink. This shows the path you used with the `--bin-dir` parameter.

     ```shell
     $ which aws
     /usr/local/bin/aws
     ```

   - Use the `ls` command to find the directory that the symlink points to. This gives you the path you used with the `--install-dir` parameter.

     ```shell
     $ ls -l /usr/local/bin/aws
     lrwxrwxrwx 1 ec2-user ec2-user 49 Oct 22 09:49 /usr/local/bin/aws -> /usr/local/aws-cli/v2/current/bin/aws
     ```

2. Delete the two symlinks in the `--bin-dir` directory. If your user account has write permission to these directories, you don't need to use `sudo`.

   ```shell
   $ sudo rm /usr/local/bin/aws
   $ sudo rm /usr/local/bin/aws_completer
   ```

3. Delete the `--install-dir` directory. If your user account has write permission to this directory, you don't need to use `sudo`.

   ```shell
   $ sudo rm -rf /usr/local/aws-cli
   ```

