#### Setting up Git Bash on Windows ####

### 1. Install Git for Windows ###

https://gitforwindows.org/

### 2. Generate an SSH key-pair ###
  1. Open Git Bash

  2. Generate key-pair (public and private keys):
  ```$ ssh-keygen -t rsa -b 4096 -C "your_email@srcs.org"
  ```

  3. When you're prompted to "Enter a file in which to save the key," press Enter.
     This accepts the default file location, usually /c/Users/<username>/.ssh/id_rsa

  4. At the prompt, just hit enter (no passphrase).

### 3. Add SSH key to ssh-agent ###
#### NOTE: this step needs to done each time you open a new Git Bash terminal window ###
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

      2. In a Git Bash terminal, cd to a directory you want your cloned project to live, then with an ssh-agent running and your private key added to the agent, run the clone command:
      ```
      $ git clone <repository-url>
      ```

  - Create a new repository on the command line:
    ```
      $ echo "# setting-up-git" >> README.md
      $ git init
      $ git add README.md
      $ git commit -m "first commit"
      $ git remote add origin git@github.com:dev-srcs/setting-up-git.git
      $ git push -u origin master
    ```

  - Push an existing repository from the command line
    ```
      $ git remote add origin git@github.com:dev-srcs/setting-up-git.git
      $ git push -u origin master
    ```

  - See local changes and what (if any) have been staged for commit:
    ```
      $ git status
    ```