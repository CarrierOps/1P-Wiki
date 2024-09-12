Using HTTPS to interact with GitHub may be easier for most actions (cloning, pushing, etc) but poses a greater sucurity threat when needing to pull code from private repos, for example, due to the need to use PATs. SSH to the rescue! All these commands will be run on windows command.

1. run `ssh-keygen -t ed25519 -C "your_email@example.com"`
2. when prompted `Enter file in which to save the key` - just press the enter key (leave it blank)
3. when prompted for a passphrase, enter a password <b>THAT YOU WILL REMEMBE</b>
4. run `start-ssh-agent`
3. run `ssh-add C:\Users\<YourUsername>\.ssh\id_ed25519`
4. run `Copytype C:\Users\YourUsername\.ssh\id_ed25519.pub | clip`. This is like doing ctrl+c, so make you don't copy anything else before completing the rest of these steps
5. Go to GitHub > settings > SSH and GPG Keys
6. Click on "New SSH key"
7. Chose a title (can be whatever)
8. set `Key type` to "Authentication Key"
9. Click in the `key` box and hit `ctrl + v`
10. Click the `Add SSH key` button