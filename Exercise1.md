## Exercise - Git basics <!-- omit in toc -->


- [Configure git](#configure-git)
- [Create/initialize a git repository](#createinitialize-a-git-repository)
- [Add a code file](#add-a-code-file)
- [Add the file to be tracked by git & stage the file](#add-the-file-to-be-tracked-by-git--stage-the-file)
- [Commit code](#commit-code)
- [Push code to GitHub](#push-code-to-github)
- [Clone some interesting repos and practice](#clone-some-interesting-repos-and-practice)
- [Create a new branch](#create-a-new-branch)

### Configure git
- Refer to the "[Config](README.md#config)" section in README
- Think of a way to organise your repositories, one way is to place all your repositories in folder called "repos" in your home folder (i.e., `C:\Users\fistlast\repos`)

###  Create/initialize a git repository

- Refer to "[Git init](README.md#git-init)" section
- [Via VSCode interface](https://code.visualstudio.com/docs/editor/versioncontrol#_initialize-a-repository)


### Add a code file

- Create a file with some text or code in it.
  - e.g.: type `print("hello")` in a Python file (file name ending in `.py`)

### Add the file to be tracked by git & stage the file

```
git add <file path>   # if the file is at the root level, file name will suffice
```
- Refer to "[Git add](README.md#git-add)" section for few more different way to stage code hunks
- [Via VSCode interface](https://code.visualstudio.com/docs/editor/versioncontrol#_commit)


### Commit code

```
git commit -m "some descriptive msg"     # provide some description, explain the code that was committed
```
- Refer to "[Git commit](README.md#git-commit)" section to see few more variations of `git commit` command
- [Via VSCode interface](https://code.visualstudio.com/docs/editor/versioncontrol#_commit)
- [Watch how to stage and commit your changes](https://www.youtube.com/watch?v=3n-_lSJ48M4)



&nbsp;


The above steps demonstrate the basic git workflow.

Next, we will save the repo to a remote server, GitHub in this case. We can use the remote server as a backup and to collaborate with others.

### Push code to GitHub

- **Fist time pushing local repo to remote server:**
  - Follow instructions at [Adding a project to GitHub without GitHub CLI](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line#adding-a-project-to-github-without-github-cli)
    - **Step 1** - [Create a new repository](https://docs.github.com/en/articles/creating-a-new-repository) on GitHub.com. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.
      - Make sure to give it same name as the repo folder on your system (this is not a strict requirement just a convention)
    - Ignore steps 2-6, we already completed these!
    - Continue with steps 7-9, make sure to copy the **SSH URL** at step 7 and use this URL in step 8
  - Via VSCode interface (only steps 8 & 9):
    - Look for `Git: Add Remote` in the VSCode command palette
    - Enter the same URL you copied in step 7 above
    - For `Remote name` use `origin` (using origin is a convention)
    - Then go to `Source Control icon` in the `Activity Bar` and click on "Publish Branch"

- **Subsequent uploads**
  - `git push`
  - Via VSCode:
    - [Watch how to push changes to remote](https://www.youtube.com/watch?v=TUYt4oXLxQs)


### Clone some interesting repos and practice

- You will be able to clone any public repo from GitHub, you can search or browse topics:
  - [GitHub topics](https://github.com/topics)
  - [Python repos](https://github.com/topics/python)
  - [mlflow repo](https://github.com/mlflow/mlflow) -- look under examples folder

- For public repos, you can use HTTPS or SSH URLs for cloning. Prefer SSH URL if you can, this avoids authentication issues if SSH is already configured.

- Via CLI - `git clone <REMOTE URL>`
- Via VSCode:
  - [Cloning a repository](https://code.visualstudio.com/docs/editor/versioncontrol#_cloning-a-repository)
  - [How to Clone a repo quick video](https://www.youtube.com/watch?v=bz1KauFlbQI)


### Create a new branch

- First thing to do before making any changes is to create a new branch.
  - Via CLI: refer to [Branch operations](README.md#branch-operations)
  - Via VSCode:
    - [Create a branch](https://code.visualstudio.com/docs/editor/versioncontrol#_branches-and-tags)
    - [How to create a branch quick video](https://www.youtube.com/watch?v=9NVFMw-MKt0)

- Work on the new branch, make changes and commit.
- You cannot push to upstream repo without proper permissions and for public repos, the workflow is slightly different. Refer to the document [Contributing to a project](https://docs.github.com/en/get-started/quickstart/contributing-to-projects)
