---
sidebar_position: 1
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";

# Course Setup

## Purpose and Goals

This guide walks you through everything you need to install and set up to be prepared for the course. After completing, you should have all the tools you need to start coding in the course.

:::note
It is entirely possible that you may already have some of these things installed. If so, just make sure to verify your installation.
:::

## Accounts to Create

Create a [GitHub Account](https://github.com/) if you don't already have one. Be sure to use a personal email address.

Additionally, apply for the [GitHub Student Developer Pack](https://education.github.com/discount_requests/application). This will give you access to free domains in which you can deploy your projects, and free credits for cloud providers so that you can host your projects.

## Things to install on your computer

### Code Editor

[Visual Studio Code (Same IDE used in CS61A)](https://code.visualstudio.com/download) for writing code.

Once you have VSCode installed, configure it so that you can open VSCode from the command line. **This is setup by default on windows**

1. Open VSCode
2. Open the Command Palette by pressing `Cmd + Shift + P` on Mac or `Ctrl + Shift + P` on Windows. Or you can View > Command Palette from the top menu.
3. Type `shell command` and select `Shell Command: Install 'code' command in PATH` from the dropdown.

Verify your installation by running the following command in terminal or powershell:

```bash
code --v #output: 1.96.2
```

### Package Manager

Package managers are tools that make it generally easier to install other pieces of software. For macOS or linux, install homebrew from the **built in terminal** which runs zsh (Z-shell). For windows, install chocolatey from the built in **powershell** application, **while running the shell as an administrator**. Then paste the following command into the terminal or powershell.

<Tabs>
  <TabItem value="Windows" label="Windows" default>
    ```bash 
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
  </TabItem>
  <TabItem value="Mac/Linux" label="Mac/Linux">
    ```bash 
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```
  </TabItem>
</Tabs>

Verify your installation by typing the following command in terminal or powershell and make sure you get output something like this:

<Tabs>
  <TabItem value="Windows" label="Windows" default>
    command:
    ```bash 
    choco
    ```
    output:
    ```bash
    Chocolatey v2.3.0
    Please run 'choco -?' or 'choco <command> -?' for help menu.
    ```
  </TabItem>
  <TabItem value="Mac/Linux" label="Mac/Linux">
    command:
    ```bash 
    brew -v
    ```
    output:
    ```bash
    Homebrew 4.3.6
    ```
  </TabItem>
</Tabs>

### A Note on Shells

The shell you use (such as bash or zsh) is different from the terminal application you use to run shell commands. This is analogous to how there are many different programming languages you can mix and match with many different text editors.

You can use any terminal application you would like, but make sure you are using bash or zsh (which is the default on mac and is almost identical to bash) as your shell for this course.

```bash
echo $0 #output: -bash or -zsh
```

If you have never used a terminal before, a safe bet is to just use the default terminal application on MacOS or Git Bash (which uses bash by default) on Windows. VSCode also has a built in terminal, which has a menu for toggling which shell you want the terminal to use.

With that being said, there are a plethora of other options available which you may want to explore later on.

<details>
  <summary>
  Why you shouldn't use PowerShell or Windows Command Shell
  </summary>

Bash is the default shell on most linux distributions, and although MacOS uses zsh by default, zsh is a direct descendent from bash and almost all commands behave the same between on both shells. PowerShell on the other hand, was developed specifically for use on Windows, and has completely different ancestry from bash. It is also not nearly as portable, widely used, or well documented as bash or zsh.

Renaming a file using bash or zsh

```bash
mv oldname.txt newname.txt
```

Renaming a file using PowerShell

```powershell
Move-Item oldname.txt newname.txt
```

Since [~96%](https://www.enterpriseappstoday.com/stats/linux-statistics.html) of the largest web servers in the world run some version of linux, it makes most sense to get familiar with scripting and a shell environment that you can use with linux.

</details>

### Git

[Git Version Control Software](https://git-scm.com/downloads) for keeping track of changes to code.

verify by running the following command in terminal or powershell:

```bash
git --version #output: git version 2.39.3
```

### GitHub CLI

We will use the GitHub command line interface to interact with GitHub from the terminal.

**Install**
<Tabs>

  <TabItem value="Windows" label="Windows" default>

```bash
choco install gh
```

  </TabItem>

  <TabItem value="Mac/Linux" label="Mac/Linux">

```bash
brew install gh
```

  </TabItem>
</Tabs>

**Verify Installation**
Don't worry if the version is not exactly the same.

```bash
gh --version #output: gh version 2.41.0
```

After installing the github cli, you will need to authenticate your github account with the cli. Run the following command in your terminal or powershell and select the option to authenticate with a browser:

```bash
gh auth login
```

Then select select Github.com, HTTPS, Yes, Login with a web browser, and copy the one-time code and paste it in the browser popup.

```bash
 ? What account do you want to log into? GitHub.com
 ? What is your preferred protocol for Git operations? HTTPS
 ? Authenticate Git with your GitHub credentials? Yes
 ? How would you like to authenticate GitHub CLI? Login with a web browser
 ! First copy your one-time code: F485-11B8
 Press Enter to open github.com in your browser...
```

Verify that you have successfully authenticated by running the following command:

```bash
gh auth status
```

Your output should look something like this:

```bash
github.com
    ✓ Logged in to github.com as aidansunbury (/Users/aidan/.config/gh/hosts.yml)
    ✓ Git operations for github.com configured to use https protocol.
    ✓ Token: gho\_****************\*\*\*\*****************
    ✓ Token scopes: gist, read:org, repo, workflow
```

Finally, configure git to use the add your correct name and email address to all of your commits.

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@gmail.com"
```

### NodeJS

[NodeJS](https://nodejs.org/en/download) allows you to run JavaScript/TypeScript code outside of the browser.

**Install**
<Tabs>
<TabItem value="Windows" label="Windows" default>

```bash
choco install nodejs --version="22.4.1"
```

</TabItem>
<TabItem value="Mac/Linux" label="Mac/Linux">
```bash
brew install node@22
```
</TabItem>
</Tabs>

**Verify Installation**
Don't worry if the version is not exactly the same.

```bash
node -v #output: v22.4.1
npm -v #output: 10.8.1
```

### Bun

[Bun](https://bun.sh/) is a package manager and alternative runtime to nodejs. We will use it primarily because it has built in support for running typescript files, and because it has quicker package install times than alternatives like npm, yarn, and pnpm.

**Install**
<Tabs>
<TabItem value="Windows" label="Windows" default>

```bash
powershell -c "irm bun.sh/install.ps1 | iex"
```

</TabItem>
<TabItem value="Mac/Linux" label="Mac/Linux">
```bash 
curl -fsSL https://bun.sh/install | bash
```
</TabItem>
</Tabs>

**Verify Installation**
Don't worry if the version is not exactly the same.

```bash
bun -v #output: 1.1.8
```

### Docker and Docker Desktop

[Docker](https://www.docker.com/) allows you to reliably reproduce the environment an application runs in on any hardware that can run the [docker engine](https://docs.docker.com/engine/). Docker Desktop provides a GUI for interacting with docker containers running locally on your machine.

Follow the install instructions for [MacOS](https://docs.docker.com/desktop/install/mac-install/) or [Windows](https://docs.docker.com/desktop/install/windows-install/) to install Docker Desktop. Installing the desktop application will also install the underlying docker engine.

Verify your installation with this command.

```bash
docker -v  #Docker version 25.0.3, build 4debf41
```

## Useful VS Code Extensions

[Install the recommended vscode extensions for the course](https://marketplace.visualstudio.com/items?itemName=CodifyBerkeley.codify-extensions). You can disable them later if you like, but give them a try! For more information, check out our [reasoning for including each one](./Bonus/extensions.mdx).

## That's it!

You are now ready to get started on our first lecture. If you have any questions about setup, ask them in the discord server so that other students can see our answers.
