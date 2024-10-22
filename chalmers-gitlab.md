# Working with Chalmers GitLab

## Access Chalmers GitLab

Open [Chalmers GitLab](https://git.chalmers.se/dashboard/projects) (git.chalmers.se). Sign in with **Chalmers Login** (ignore the username/password fields):

![chalmers-gitlab-sign-in.png](img/chalmers-gitlab-sign-in.png)

You will see all your current projects. If a lab project is missing, it could be because:

- The lab has not yet been published.
- An invitation was sent to your Chalmers student address, but you have not yet accepted it.
- The lab is done in groups and you have not [joined a lab group](lab-info.md#joining-a-group).

If you still do not see the project after refreshing 5 minutes later, our systems are down. Let us know!

## Configure your account

GitLab will notify you about new lab projects and gradings of your submissions via your Chalmers student address. You can change this by [adding an email address](https://git.chalmers.se/-/profile/emails) and then setting this as the [notification email](https://git.chalmers.se/-/profile/notifications). **Make sure to configure an email address you actually read.**

You can also [set your name](https://git.chalmers.se/-/profile) and a profile picture, if you wish.

### Set up an SSH key

You will use git to synchronize your local work with the lab project on Chalmers GitLab. For this, you need an SSH key ([explained here](https://git.chalmers.se/help/user/ssh.md)). Here is a short summary:

1. If you have not generated an SSH key before: open a terminal and run `ssh-keygen`, leaving all input prompts empty (we recommend an empty password).
2. The public part of your key is stored relative to your home directory in `.ssh/id_<something>.pub`. Open it in a text editor and copy its content (so you can paste it in your browser).
3. Go to [SSH keys on Chalmers GitLab](https://git.chalmers.se/-/user_settings/ssh_keys) and add a new key, pasting the contents of the above file.
4. Check your setup by running `ssh -T git@git.chalmers.se` in your terminal. You may be prompted to confirm the authenticity of the host. The command should then print a welcome sentence.

If you have any problems, ask on Discord or talk to a teaching assistant during lab supervision.

**Note**: If you use the Chalmers lab computers, you may experience a problem with git cloning. This is due to the following:

- `ssh-keygen` puts the key in `.ssh` in your user folder on the C drive.
- git looks for your key in `.ssh` in your Z drive.

To solve this, just copy over the `.ssh` directory from your user folder on the C drive to the Z drive.

## Work on a lab

For each lab assignment, we add you as a developer to a project on Chalmers GitLab. Scrolling down past the file listing, you will see the lab description (this is the file `README.md`, written in Markdown). You can use this project as you see fit (issues, merge requests, etc.), but mainly it consists of a **git repository**. For group projects, you can choose how to collaborate: together on one computer or everyone using their own computer and using git to synchronize changes.

Each lab comes with specific instructions on what you should implement and what questions you should answer (in `answers.txt`). Please do not change the signatures or behaviour of pre-existing methods unless instruncted as it will make your submission harder for us to test and grade. Of course, you are allowed to add things that do not affect the existing functionality (new variables, functions, methods, classes, and, most importantly, comments).

### Use git

[Git](https://en.wikipedia.org/wiki/Git) is the industry standard for version control and collaborative software development. Make sure [it is installed](https://git.chalmers.se/help/topics/git/how_to_install_git/index.md) on your system and working. It will pay off to [become familiar](https://git.chalmers.se/help/gitlab-basics/start-using-git.md) with it!

To interact with the provided git repository, you have several options:

- [Clone](https://git.chalmers.se/help/gitlab-basics/start-using-git.md#clone-with-ssh) the git repository via SSH:

  ![chalmers-gitlab-clone-ssh.png](img/chalmers-gitlab-clone-ssh.png)

  Each time you want to do some work in your local copy:
    - `git pull` to [pull](https://git.chalmers.se/help/gitlab-basics/start-using-git.md#download-the-latest-changes-in-the-project) the latest changes other group members might have done,
    - `git add -u` and `git commit` to [add and commit](https://git.chalmers.se/help/gitlab-basics/start-using-git.md#add-and-commit-local-changes) your own changes,
    - `git push` to [push](https://git.chalmers.se/help/gitlab-basics/start-using-git.md#send-changes-to-gitlabcom) to GitLab.

  For a summary of useful commands, see the [git cheatsheet](https://about.gitlab.com/images/press/git-cheat-sheet.pdf).

- If you use an IDE such as IntelliJ or Eclipse, it comes with built-in git integration. For example, in IntelliJ, simply create a project using ***File → New → Project from Version Control*** and paste the repository SSH URL you get from the project page by clicking on ***Clone***.

  **Note**: If IntelliJ highlights lots of strange errors after cloning, you need to set up the project SDK (any recent version will do):

  ![intellij-setup-java.png](img/intellij-setup-java.png)

  Alternatively, go to ***File → Project Stucture...*** and specify a Project SDK version.

To simplify things, we suggest you only use the default branch (called ***main***) and do not create extra branches. Then you won't have to interact with the branching functionality of git.

### Switching programming language

Each lab is offered in two version: Java and Python. You can choose which one to work with. If you just open the project, you get the Python version. To switch to Java, read on.

There are branches ***java*** and ***python*** in your project. You can have a look at them, but they cannot be modified (they represent the starting state that your submission will be compared against). Instead, you work on the default branch ***main***. By default, it points to ***python***. To change it to Java, you can run the following git commands:

- `git switch --force-create main origin/java`
- `git push --set-upstream --force origin main`

**Warning**: this will erase all previous work on branch ***main***. You can make a backup beforehand if desired:

- `git branch main-backup main`

### Robograder

We contracted elite roboticists to build 
<span style="background-color: #ffff00;">R</span><span style="background-color: #ffaf40;">o</span><span style="background-color: #ff8080;">b</span><span style="background-color: #ff40af;">o</span><span style="background-color: #ff00ff;">g</span><span style="background-color: #af40ff;">r</span><span style="background-color: #8080ff;">a</span><span style="background-color: #40afff;">d</span><span style="background-color: #00ffff;">e</span><span style="background-color: #4fffaf;">r</span>™. 
You should **test your code** with Robograder to iron out bugs before you submit. To call Robograber, create a tag like you would for a submission (explained below). But use a **test tag**, starting with `test` (for example `testPlzKThx`). Robograder will respond with an issue in your project. Often it is fast, but it can take up to 15 minutes. You should be notified by email (see above how to set this up).

You are allowed to use Robograder **five times** for each lab. This limitation is to prevent test spamming and encourage you to think instead.

## Submit a lab

We use the **tags** feature of git for lab submission. When you are ready to submit, go to your project page on GitLab and create a tag:

![create-tag.png](img/create-tag.png)

The name of a **submission tag** must start with `submission` (make sure to spell correctly). If you want to be nice, add a number (0, 1, 2, …) to indicate your submission attempt. Example:

![create-tag-details.png](img/create-tag-details.png)

You can write a submission comment in the message field.

Once you have created a submission tag, you cannot change it: it serves as your proof of submission. You can still push new commits to the repository, but this won't change the tagged version of your code (the commit the tag points to). Therefore, make sure to tag exactly the version you mean to hand in (be extra careful if you work with multiple branches). If you accidentally put the tag in the wrong place, you can use a new tag. For example, if `submission0` ended up on the wrong commit, put `submission1` on the right one and we will ignore the previous tag.

**Note**: The tag must live in the Chalmers GitLab repository, not just your local git clone. If you create the tag locally and then push, make sure to **push tags**.

You can check your submission by visiting ***Repository → Tags***. The submission tag should be highlighted as 
<span style="background-color: #bfedd2; color: #006000; padding: 0 10px; border-radius: 10px">protected</span>:

![show-tags.png](img/show-tags.png)

## Get feedback

After you submit a lab, we add you to a special **grading merge request** for your submission. There you can see the grading status of all your submissions. The graders will give their feedback by commenting in this merge request (you should be notified by email).

- Use the **discussion thread** in the merge request to respond to the feedback, ask for clarifications, or complain about the grading. Your grader will respond.

If you did not pass in the first grading and wish to resubmit, create a new submission tag (e.g. `submission1`).
