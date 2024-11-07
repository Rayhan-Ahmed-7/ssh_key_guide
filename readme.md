Here's the updated README with additional notes for `rsa` commands, where applicable, for users on legacy systems:

---

# SSH Key Setup for GitHub

This guide provides step-by-step instructions for generating an SSH key, adding it to the SSH agent, and linking it to your GitHub account. Instructions are provided for both **Ubuntu** and **Windows**.

---

## Table of Contents

- [Generating SSH Key](#generating-ssh-key)
- [Starting SSH Agent](#starting-ssh-agent)
- [Printing SSH Key](#printing-ssh-key)
- [Adding SSH Key to GitHub](#adding-ssh-key-to-github)
- [Testing the SSH Connection](#testing-the-ssh-connection)

---

## Generating SSH Key

> **Note:** If you are using a legacy system that doesn't support the `Ed25519` algorithm, use:
>
> ```bash
> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```

### Ubuntu

1. Open the terminal.
2. Run the following command to generate a new SSH key pair:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   Replace `"your_email@example.com"` with the email address associated with your GitHub account.

   > **Note:** For legacy systems, use:
   >
   > ```bash
   > ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   > ```

3. When prompted to enter a file in which to save the key, press **Enter** to accept the default location.
4. When prompted to create a passphrase, you can press **Enter** if you don’t want to set a passphrase. Otherwise, type a secure passphrase.

### Windows

1. Open **PowerShell**.
2. Run the following command to generate a new SSH key pair:

   ```powershell
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   Replace `"your_email@example.com"` with your GitHub email.

   > **Note:** For legacy systems, use:
   >
   > ```powershell
   > ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   > ```

3. When prompted to enter a file in which to save the key, press **Enter** to accept the default location.
4. When prompted to create a passphrase, you can press **Enter** if you don’t want a passphrase, or enter a secure passphrase.

---

## Starting SSH Agent

### Ubuntu

1. Start the SSH agent by running:

   ```bash
   eval "$(ssh-agent -s)"
   ```

2. Add the SSH key to the agent:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

   > **Note:** For `rsa`, use:
   >
   > ```bash
   > ssh-add ~/.ssh/id_rsa
   > ```

### Windows

1. Start the SSH agent by running:

   ```powershell
   Start-Service ssh-agent
   ```

2. Add the SSH key to the agent:

   ```powershell
   ssh-add $env:USERPROFILE\.ssh\id_ed25519
   ```

   > **Note:** For `rsa`, use:
   >
   > ```powershell
   > ssh-add $env:USERPROFILE\.ssh\id_rsa
   > ```

---

## Printing SSH Key

To add the SSH key to GitHub, you need to copy it to your clipboard.

### Ubuntu

1. Print the SSH key in the terminal:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

   > **Note:** For `rsa`, use:
   >
   > ```bash
   > cat ~/.ssh/id_rsa.pub
   > ```

2. Select and copy the entire key that is displayed.

### Windows

1. Print the SSH key in PowerShell:

   ```powershell
   Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
   ```

   > **Note:** For `rsa`, use:
   >
   > ```powershell
   > Get-Content $env:USERPROFILE\.ssh\id_rsa.pub
   > ```

2. Copy the entire output.

---

## Adding SSH Key to GitHub

1. Go to [GitHub SSH settings](https://github.com/settings/keys).
2. Click on **New SSH key**.
3. In the **Title** field, add a label for your key (e.g., "Ubuntu Laptop" or "Windows Desktop").
4. Paste your SSH key into the **Key** field.
5. Click **Add SSH key**.

---

## Testing the SSH Connection

To ensure everything is set up correctly, test the SSH connection to GitHub:

```bash
ssh -T git@github.com
```

You should see a success message if the connection is working.

---

You have successfully set up an SSH key and connected it to GitHub!
