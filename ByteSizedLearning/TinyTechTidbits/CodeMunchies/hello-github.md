# Getting Started With GitHub

## Introduction

### What is Git?
Git is a version control tool that allows you to take snapshots of your files. You can track changes made since the last snapshot track every file in a repository (folder) including sub-folders. It always you to develop in parallel using branches (more of this later❗). You can connect & save your git repository anywhere (GitHub) and collaborate with others on the same codebase/files.

### What is GitHub?

GitHub is a place to host our git repositories. It acts as a “Source of Truth” for our codebase. GitHub provides a solution to the following questions.

- How do I share my code with others?
- How do I work on the same code with others?
  
GitHub also provides many additional features such as:

- Security
- User management
- Github actions
- And much much much more!

**Note:** There is a GitHub Desktop application that can be used to perform some of the operations in the next section; however, it is highly recommended to use and get familiar with the command line.


## Common Commands

- `git init`: This command converts any directory into a Git Repository. This command is needed to start a git project starting from as local directory. For some more details on this command visit the [Official GitHub Documentation](https://github.com/git-guides/git-init) 👀.


- `git clone`: This command allows you to clone a GitHub Repository so that you have the ability to work on a code repository with others and be able to make changes to and receive changes from others. When you clone a repository, you copy the repository from GitHub.com to your local machine. Cloning a repository pulls down a full copy of all the repository data that GitHub.com has at that point in time, including all versions of every file and folder for the project. Here is an example of cloning using the `1P Wiki`.

  **ex:** ```git clone https://github.com/CarrierOps/1P-Wiki.git ```

- `git status`: This command shows you any changes that you have made to your current repository such as modifying, adding, or deleting files. After making edits to this file that you are currently reading, you'd see something like this when running this command.

<figure align="center">
    <img src="../../../imgs/git status example.png" width="100%">
  <figcaption>git status</figcaption>
</figure>




- `git add`: This command allows you to specify which which changes you want to add to the repository. The add commands also sets up the `git commit` as all of the files added with be apart of the save point created by `git commit`. For example, if I wanted to add the change made to this current file as seen in the ***git status*** figure, you can use the following command

  **ex:** `git add ByteSizedLearning/TinyTechTidbits/CodeMunchies/hello-github.md`

  **Pro Tip 😎:** 
You can use `git add .` to add all changes made at once with one command. This is the most often command used when adding, but it's still good to know how to add individual changes.

  **Try This:** Try running the `git status` command after adding to see what changes 👀.

- `git commit`: The commit command effectively acts as a save point for the code/repository. Commits keep track and locally save changes made. When committing changes, it is best practice to add a message indicated by the `-m` as seen in the command below 📬.

  **ex:** `git commit -m " I made changes to the hello-github markdown file " `



- `git push`:  This command applies the changes made locally on   your machine/version of the repository to the repository on GitHub. This allows others to now see those changes and access them. Here's the command I would run to push the changes I made in this file to the repository of Github 🫸.

  **ex:** `git push origin`

  **Pro Tip 😎:** The `origin` command is an alias name for the remote repository that a project was originally cloned from. This is much easier than rewriting out the repository again.

- `git pull`: This command gets the latest version of the GitHub repository with all the latest edits and makes sure that your local version has all of those changes. Here's the command I would run to pull the changes others have made to this repository 🫷 .

  **ex:** `git pull origin`

  **Note:** `git pull` is the combination of a `git fetch` and `git merge`. More information of these 2 commands can be found [here](https://git-scm.com/docs/git-fetch) and [here](https://git-scm.com/docs/git-merge).




- `git branch`: This command tells you what branch you are currently on in your repository. Please read the [Importance Of Branching](#importance-of-branching) section to understand branches and how to check which branch you on are. To quickly check which branch you are currently on, use the following command.

  **ex:** `git branch`

- `git checkout`: If you want to switch branches, you can use the this command. For example, let's say I had a brach called `Michael's Branch`. I can switch to this branch using the following command:
`git checkout "Michael's Branch"` .
To create a new branch, you can using the `git checkout -b` command. As an example, if I wanted to make a branch called `Example Branch` I could using the following command:
`git checkout -b "Example Branch"`. It generally isn't best practice to have spaces between in your branch names, so it's a good idea to separate them with either _ or - . However, if you want to have spaces, you can use "" to create or switch to a branch that has spaces in them.



- `git clean`: This command allows you to remove specific changes or files that you added and do not want to have pushed to GitHub. There are a lot of different variations of this command. To see all of them, click [here](https://git-scm.com/docs/git-clean) 👀. A good starter one would be the interactive variation command. You often have to do this if after a `git add` and you want to remove those adds. 
**ex:** `git clean -i`

  **Note:** You may have to use different variations depending on the situation.

- `git restore`: This command allows you to restore back to the latest version of the repository that you had by reverting back all changes made. This is very useful for making quick edits to a code for testing purpose but not wanting to have those changes present in the repository. As an example, if you wanted to restore this exact file to the point before any changes were made, you could use the following command.

  **ex:** 
`git restore ByteSizedLearning/TinyTechTidbits/CodeMunchies/hello-github.md`

  **Pro Tip 😎:** Use `git restore .` to restore all changes to the latest version you have of the code base. Effectively, if you run `git status` and you don't want any of those changes made or you want to undo all of those changes, run `git restore .`
- `git diff`: This command will show you all of the changes that were made in your working directory. It's similar to the command `git status` but it will give you a lot more detail. Running the `git diff` command will show you all of the every single change made. Green indicates an addition while red indicates a deletion. Keep pressing enter in the command line to see all of the changes until you see `End`. At this point, if you want to exit the the pager, press **q** on your keyboard to return back to the command line. For more info about the different types of `git diff` you can use, visit the [Official Git Documentation](https://git-scm.com/docs/git-diff) 👀.



## Importance Of Branching
A `branch` in GitHub is in really simple terms, another copy of the repository. Branches are very important however, as it allows us develop independently of other branches. This is very useful as lets us develop, fix bugs, and add new features while keeping the functionality of the main branch active. Here's analogy of why branching is important. Lets say you have a cookie company 🍪, and customers really like your cookies. However, you want to try and experiment and try out some new flavours/ideas with your cookies. As a good cookie company owner, you won't apply these changes to your products immediately as you would probably want people to test your new cookie ideas before sending them out to the market. This is the same idea with code and branches. You want your `main` or `prod`(production branch) always working well, but you can experiment and fix things in the `dev`(developer branch) or other sub-branches. 

<figure align="center">
    <img src="../../../imgs/Git Branches.png" width="100%">
  <figcaption>Git Branches</figcaption>
</figure>




## Github Actions
GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. Please visit the [GitHub Markdown](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/Description%20Of%20Services/GitHub.md) for further reading. You can also visit the offical [GitHub Documentation](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) for a fully comprehensive explanation of GitHub actions and how to use them.



<!-- 
## More advanced later -> Move these up!!!
- init
- checkout
- checkout -b
- switch
- diff
- diff with flags?
- git blame
- 
-  -->













