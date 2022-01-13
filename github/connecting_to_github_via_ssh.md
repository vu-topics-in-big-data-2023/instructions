# Connecting to Github using SSH

[https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) contains the official github documentation for how to set this up.
This is highly recommended.

## Section 1. About SSH

Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username and personal access token at each visit.

When you set up SSH, you'll [generate an SSH key and add it to the ssh-agent](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and then [add the key to your GitHub account](https://docs.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account). Adding the SSH key to the ssh-agent ensures that your SSH key has an extra layer of security through the use of a passphrase. For more information, see "[Working with SSH key passphrases](https://docs.github.com/en/articles/working-with-ssh-key-passphrases)."

To use your SSH key with a repository owned by an organization that uses SAML single sign-on, you'll need to authorize it first. For more information, see "[Authorizing an SSH key for use with SAML single sign-on](https://docs.github.com/en/articles/authorizing-an-ssh-key-for-use-with-saml-single-sign-on)."

We recommend that you regularly [review your SSH keys list](https://docs.github.com/en/articles/reviewing-your-ssh-keys) and revoke any that are invalid or have been compromised.

If you haven't used your SSH key for a year, then GitHub will automatically delete your inactive SSH key as a security precaution. For more information, see "[Deleted or missing SSH keys](https://docs.github.com/en/articles/deleted-or-missing-ssh-keys)."

If you're a member of an organization that provides SSH certificates, you can use your certificate to access that organization's repositories without adding the certificate to your GitHub account. For more information, see "[About SSH certificate authorities](https://docs.github.com/en/articles/about-ssh-certificate-authorities)."

## Section 2. Checking for existing SSH keys

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

**Note:** DSA keys (SSH-DSS) are no longer supported. Existing keys will continue to function, but you cannot add new DSA keys to your GitHub account.

### For Mac Users

1. Open Terminal (for Mac and Linux users), or Git Bash (for Windows Users)

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present:

   ```shell
   $ ls -al ~/.ssh
   # Lists the files in your .ssh directory, if they exist
   ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of the public keys are one of the following:

- *id_rsa.pub*
- *id_ecdsa.pub*
- *id_ed25519.pub*

If you don't have an existing public and private key pair, or don't wish to use any that are available to connect to GitHub, then [generate a new SSH key](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

If you see an existing public and private key pair listed (for example *id_rsa.pub* and *id_rsa*) that you would like to use to connect to GitHub, you can [add your SSH key to the ssh-agent](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#adding-your-ssh-key-to-the-ssh-agent).

**Tip:** If you receive an error that *~/.ssh* doesn't exist, don't worry! We'll create it when we [generate a new SSH key](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

## Section 3. Generating a new SSH key and adding it to the ssh-agent

After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.

If you don't already have an SSH key, you must [generate a new SSH key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key). If you're unsure whether you already have an SSH key, check for [existing keys](https://docs.github.com/en/articles/checking-for-existing-ssh-keys).

If you don't want to reenter your passphrase every time you use your SSH key, you can [add your key to the SSH agent](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent), which manages your SSH keys and remembers your passphrase.

### [Generating a new SSH key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)

1. Open Terminal.

2. Paste the text below, substituting in your GitHub email address.

   ```shell
   $ ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   **Note:** If you are using a legacy system that doesn't support the Ed25519 algorithm, use:

   ```shell
   $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

   This creates a new ssh key, using the provided email as a label.

   ```shell
   > Generating public/private ed25519 key pair.
   ```

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

   ```shell
   > Enter a file in which to save the key (/Users/you/.ssh/id_ed25519): [Press enter]
   ```

4. At the prompt, type a secure passphrase. For more information, see ["Working with SSH key passphrases"](https://docs.github.com/en/articles/working-with-ssh-key-passphrases).

   ```shell
   > Enter passphrase (empty for no passphrase): [Type a passphrase]
   > Enter same passphrase again: [Type passphrase again]
   ```

### [Adding your SSH key to the ssh-agent](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)

Before adding a new SSH key to the ssh-agent to manage your keys, you should have [checked for existing SSH keys](https://docs.github.com/en/articles/checking-for-existing-ssh-keys) and [generated a new SSH key](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key). When adding your SSH key to the agent, use the default macOS `ssh-add` command, and not an application installed by [macports](https://www.macports.org/), [homebrew](http://brew.sh/), or some other external source.

1. Start the ssh-agent in the background.

   ```shell
   $ eval "$(ssh-agent -s)"
   > Agent pid 59566
   ```

2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain.

   - First, check to see if your `~/.ssh/config` file exists in the default location.

     ```shell
     $ open ~/.ssh/config
     > The file /Users/you/.ssh/config does not exist.
     ```

   - If the file doesn't exist, create the file.

     ```shell
     $ touch ~/.ssh/config
     ```

   - Open your `~/.ssh/config` file, then modify the file, replacing `~/.ssh/id_ed25519` if you are not using the default location and name for your `id_ed25519` key.

     ```
     Host *
       AddKeysToAgent yes
       UseKeychain yes
       IdentityFile ~/.ssh/id_ed25519
     ```

     **Note:** If you chose not to add a passphrase to your key, you should omit the `UseKeychain` line.

3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace *id_ed25519* in the command with the name of your private key file.

   ```shell
   $ ssh-add -K ~/.ssh/id_ed25519
   ```

   **Note:** The `-K` option is Apple's standard version of `ssh-add`, which stores the passphrase in your keychain for you when you add an ssh key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the `-K` option.

   If you don't have Apple's standard version installed, you may receive an error. For more information on resolving this error, see "[Error: ssh-add: illegal option -- K](https://docs.github.com/en/articles/error-ssh-add-illegal-option-k)."

4. [Add the SSH key to your GitHub account](https://docs.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account).

## Section 4. Adding a new SSH key to your GitHub account

To configure your GitHub account to use your new (or existing) SSH key, you'll also need to add it to your GitHub account.

Before adding a new SSH key to your GitHub account, you should have:

- [Checked for existing SSH keys](https://docs.github.com/en/articles/checking-for-existing-ssh-keys)
- [Generated a new SSH key and added it to the ssh-agent](https://docs.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

After adding a new SSH key to your GitHub account, you can reconfigure any local repositories to use SSH. For more information, see "[Switching remote URLs from HTTPS to SSH](https://docs.github.com/en/articles/changing-a-remote-s-url/#switching-remote-urls-from-https-to-ssh)."

**Note:** DSA keys (SSH-DSS) are no longer supported. Existing keys will continue to function, but you cannot add new DSA keys to your GitHub account.

1. Copy the SSH public key to your clipboard.

   If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

   ```shell
   $ pbcopy < ~/.ssh/id_ed25519.pub
   # Copies the contents of the id_ed25519.pub file to your clipboard
   ```

   **Tip:** If `pbcopy` isn't working, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.

2. In the upper-right corner of any page, click your profile photo, then click **Settings**.

   ![Settings icon in the user bar](https://docs.github.com/assets/images/help/settings/userbar-account-settings.png)



3. In the user settings sidebar, click **SSH and GPG keys**.

   ![Authentication keys](https://docs.github.com/assets/images/help/settings/settings-sidebar-ssh-keys.png)



4. Click **New SSH key** or **Add SSH key**.

   ![SSH Key button](https://docs.github.com/assets/images/help/settings/ssh-add-ssh-key.png)



5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

6. Paste your key into the "Key" field.

   ![The key field](https://docs.github.com/assets/images/help/settings/ssh-key-paste.png)



7. Click **Add SSH key**.

   ![The Add key button](https://docs.github.com/assets/images/help/settings/ssh-add-key.png)



8. If prompted, confirm your GitHub password.

   ![Sudo mode dialog](https://docs.github.com/assets/images/help/settings/sudo_mode_popup.png)
