# Setting up SSH  with GitHub

Using HTTPS to interact with GitHub may be easier for most actions (cloning, pushing, etc) but poses a greater security threat when needing to pull code from private repos, for example, due to the need to use PATs. SSH to the rescue! All these commands will be run on Windows Command.

1. open Git Bash

2. Run `ssh-keygen -t ed25519 -C "your_email@example.com"`
   - When prompted:
     - **Enter file in which to save the key:** Just press Enter (leave it blank).
     - **Enter a passphrase:** Enter a password **THAT YOU WILL REMEMBER**.

3. Run `eval $(ssh-agent -s)`

4. Run `ssh-add -c C:\Users\<YourUsername>\.ssh\id_ed25519`
   - The `-c` ensures you are prompted for the passphrase every time the key is used.

5. Open windows command prompt (cmd)

6. Run `type C:\Users\<YourUsername>\.ssh\id_ed25519.pub | clip`
   - This copies the public key to your clipboard. **Don't copy anything else before completing the next steps.**

7. Go to GitHub > Settings > SSH and GPG Keys:
   - Click on **New SSH key**.
   - Choose a title (can be anything).
   - Set **Key type** to **Authentication Key**.
   - Click in the key box and hit **Ctrl + V**.
   - Click the **Add SSH key** button.

8. Test the SSH connection:
   - Run `ssh -T git@github.com`
   - If successful, you'll see a message like:
     `Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.`
      - If instead you see this message:
         `Are you sure you want to continue connecting (yes/no/[fingerprint])?` then type `yes` then hit \<enter>
      - provide your passphrase if prompted for it

add verification:

``` bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgSign true
```
