## Git Bash on Windows: Set Up and Basic Usage

### 1. Install Git for Windows ###

https://gitforwindows.org/

### 2. Generate an SSH key-pair ###
  1. Open Git Bash

  2. Generate key-pair (public and private keys):
  ```
  $ ssh-keygen -t rsa -b 4096 -C "your_email@srcs.org"
  ```

  3. When you're prompted to "Enter a file in which to save the key," press Enter.
     This accepts the default file location, usually /c/Users/<username>/.ssh/id_rsa

  4. At the prompt, just hit enter (no passphrase).

### 3. Add SSH key to ssh-agent ###
#### NOTE: this step needs to done each time you open a new Git Bash terminal window
  1. Start an ssh-agent background process:
  ```
    $ eval $(ssh-agent -s)
  ```

  2. Add your private key to the agent:
  ```
    $ ssh-add ~/.ssh/id_rsa
  ```

  3. Verify your key has been added to running agent:
  ```
    $ ssh-add -l
  ```

  ### 4. Add your SSH public key to your GitHub account. ###
  1. Still within Git Bash terminal, copy your public SSH key to the clipboard:
  ```
    clip < ~/.ssh/id_rsa.pub
  ```

  2. Log into your github.com account.

  3. In the upper-right corner of any page, click your profile photo, then click Settings.

  4. In the user settings sidebar, click SSH and GPG keys.

  5. Click New SSH key or Add SSH key.

  6. In the "Title" field, add a descriptive label for the new key. For example, if you're using a school computer, you might call this key "Java 101 laptop".

  7. Paste your key into the "Key" field.

  8. Click Add SSH key.

### Basic Workflow Tasks ###
  - Clone a repository (Clone with SSH)
      1. In github.com on the main page of the project you'd like to clone, click on the green 'Clone or download' button and copy the 'Clone with SSH' url to the clipboard.

      2. In a Git Bash terminal, cd to a directory where you want your cloned project to live, then with an ssh-agent background process running and your private key added to the agent, run the command:
      ```
        $ git clone <github-repository-url>
      ```
  - After cloning project, to begin working, change into the project root directory.  
    Within your project root directory there is a hidden folder '.git' which contains all the
    repository configuration as well as full local copy of repository.
    ```
      $ cd /path/to/<myproject-folder>
    ```

  - Create a new github repository:
      1. Log into your account on github.com and create a new project.  Do not
         initialize the repository with a README and do not add a .gitignore (yet).

      2. Create directory with same name as your newly created project.
         This will be your project root folder. cd into the directory and
         run these command:

      ```
        $ echo "# setting-up-git" >> README.md
        $ git init
        $ git add README.md
        $ git commit -m "first commit"
        $ git remote add origin <github-repository-url>
        $ git push -u origin master
      ```
      3. You may also need to add a .gitignore file to tell git to ignore certain
         files and directories. Example:
          ```
            /.gradle/
            /bin/
            build/
            *.pdf
            *.csv
            *.properties
            *.exe
          ```

  - Push an existing repository from the command line
    ```
      $ git remote add origin <github-repository-url>
      $ git push -u origin master
    ```

  - Grab the latest version of project from remote repository.  If you have made
    any local commits and not pushed them yet, you may need to merge. If you have
    staged ('added') files but not committed, you will first need to do a commit
    or revert the changes before you can pull.
    #### NOTE: all the basic commands that follow are best executed from your
               project root folder.
    ```
      $ cd /path/to/<project-root-folder>
      $ git pull
    ```

  - See list of locally modified files and what (if any) have been staged for commit:
    ```
      $ git status
    ```

  - Stage files for commit. List individually or use wildcard:
    ```
      $ git add <file>
    ```

  - Commit changes with message describing changes:
    ```
      $ git commit -m "some message"
    ```

  - Push your commit(s) to remote repository:
    ```
       $ git push -u origin master
    ```

  - For additional commands:
    ```
      $ git help
    ```
