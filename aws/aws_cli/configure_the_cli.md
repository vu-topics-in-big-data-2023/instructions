# Configure the AWS CLI

**Note**: this file merely covers critical steps of configuring the AWS CLI. To learn more details about AWS CLI setup, please see: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html.

The AWS CLI stores sensitive credential information that you specify with `aws configure` in a local file named `credentials`, in a folder named `.aws` in your home directory. The less sensitive configuration options that you specify with `aws configure` are stored in a local file named `config`, also stored in the `.aws` folder in your home directory. Thus, at the end of the configuration steps, you should have the following files in the `.aws` directory.

```shell
$ ls ~/.aws
credentials
config
```

## Create `~/.aws/credentials` file

For aws educate account, you can find access key ID, secret access key, and session token values from [vocareum](https://labs.vocareum.com/home/login.php?code=&e=You%20are%20not%20logged%20in.%20Please%20login) main page > Account details > AWS CLI > Show.

![Screen Shot 2021-01-21 at 3.27.42 PM 2](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-21 at 3.27.42 PM 2.png)

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

![Screen Shot 2021-01-21 at 3.10.01 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-21 at 3.10.01 PM.png)

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
