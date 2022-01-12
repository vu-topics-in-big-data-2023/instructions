# AWS CLI

[Official Documentation](https://docs.aws.amazon.com/cli/index.html)

# Important
- Use AWS cli **version 2.x**
- Please use AWS Educate Account responsibly.
Remember to shut down your instances when not in use to make the best use of your credits.
And, don't forget to logout once you are done with your work!

# What is AWS CLI?
https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html

The AWS Command Line Interface (AWS CLI) is an open source tool that enables you to interact with AWS services using commands in your command-line shell. With minimal configuration, the AWS CLI enables you to start running commands that implement functionality equivalent to that provided by the browser-based AWS Management Console from the command prompt in your terminal program:

- **Linux shells** – Use common shell programs such as [bash](https://www.gnu.org/software/bash/), [zsh](http://www.zsh.org/), and [tcsh](https://www.tcsh.org/) to run commands in Linux or macOS.

- **Windows command line** – On Windows, run commands at the Windows command prompt or in PowerShell.

- **Remotely** – Run commands on Amazon Elastic Compute Cloud (Amazon EC2) instances through a remote terminal program such as PuTTY or SSH, or with AWS Systems Manager.

# Installing AWS CLI

[Official AWS Installation Instructions](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

# Configuring AWS CLI
[Official AWS quick set-up instructions](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html)
[Official AWS configuration file settings](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)

# TODO:screenshot of gettings aws cli info from AWS Learner Academy labs

As stated in the image, create the file `~/.aws/credentials`, and copy all contents in the box to it.

```shell
$ nano ~/.aws/credentials

# copy all contents in the box shown above into the file
[default]
aws_access_key_id=xxxxx
aws_secret_access_key=xxxxx
aws_session_token=xxxxx

# Hit Ctrl+x
# Enter y to save the modification
```

**!!! Note** the credential information shown above changes whenever you re-login the AWS Educate account. So you have to rewrite the `~/.aws/credentials` file.

## Create `~/.aws/config` file

Then, we'll add the default rejion name and output format in the config file.

To identify the default AWS Region to send requests to for commands requested using this profile, please login your AWS Console from the vocareum main page:

# TODO: screenshot of getting region info

Then, you can see the default region name. For instance, here, my default region name is us-east-1.

Replace the region name with your own values.

```shell
$ nano ~/.aws/config

# copy the following contents into the config file
[default]
region=xxxxx
output=json

# Hit Ctrl + x
# Enter 'y' to save modification
```
