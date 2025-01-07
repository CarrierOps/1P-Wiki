# Setting up SSH  with GitHub

Using HTTPS to interact with GitHub may be easier for most actions (cloning, pushing, etc) but poses a greater security threat when needing to pull code from private repos, for example, due to the need to use PATs. SSH to the rescue! All these commands will be run on Windows Command.

1. Run `ssh-keygen -t ed25519 -C "your_email@example.com"`
   - When prompted:
     - **Enter file in which to save the key:** Just press Enter (leave it blank).
     - **Enter a passphrase:** Enter a password **THAT YOU WILL REMEMBER**.

2. Run `start-ssh-agent`

3. Run `ssh-add -c C:\Users\<YourUsername>\.ssh\id_ed25519`
   - The `-c` ensures you are prompted for the passphrase every time the key is used.

4. Run `type C:\Users\<YourUsername>\.ssh\id_ed25519.pub | clip`
   - This copies the public key to your clipboard. **Don't copy anything else before completing the next steps.**

5. Go to GitHub > Settings > SSH and GPG Keys:
   - Click on **New SSH key**.
   - Choose a title (can be anything).
   - Set **Key type** to **Authentication Key**.
   - Click in the key box and hit **Ctrl + V**.
   - Click the **Add SSH key** button.

6. Test the SSH connection:
   - Run `ssh -T git@github.com`
   - If successful, you'll see a message like: 
     `Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.`
