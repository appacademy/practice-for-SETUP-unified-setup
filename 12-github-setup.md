# GitHub Setup

## Getting Started with git

### What is git?

> Git is a free and open source distributed version control system designed to
> handle everything from small to very large projects with speed and efficiency.

git is a software program much like *MS Word* or *Google Chrome* but it is part
of a class of programs known as **cli tools**. This program does not have a user
interface (UI) like most programs we are familiar with, but instead is
accessible primarily through our **command line** / **terminal**.

Being accessible primarily only through the **command line**/**terminal** sounds
like a huge restriction, but it allows us as developers to use it for what it's
good at and for it to then quickly go away.

So what does git do? Well it is a *Version Control System* or **VCS**. It keeps
track of a set of files over time.

Each time changes need to get recorded, they are wrapped in a 'commit' and that
commit is saved to the repository (or repo) as a snapshot of the files at that
time. The tracking and reconciling abilities that git has to handle conflicts
makes git an effective tool for many developers to work on the same codebase at
the same time, as well as to record the history of a project in case an issue is
introduced.

### What is GitHub?

Github is a company that provides hosting for git repositories. It works
together with the git cli tools to manage the codebase by making or deleting
branches, creating pull requests, and sharing the git project with other
developers.

---

## Installing git

### Windows

If you have WSL already setup and are using an Ubuntu distribution, you already
have git within linux! If you are using a different distribution you may need to
manually install git.

While you don't need git installed in Windows, you do need to have the
git-credential-manager-core installed. It comes bundled with git so you can
easily install it in Windows by using the installer found [here][git-win].

Once you've downloaded one of the "Git for Windows Setup" distributions (either
32-bit or more likely 64-bit) you can launch the installer and accept all the
defaults.

Now that git-credential-manager-core is installed, you can restart your terminal
and continue on working through this guide.

### Mac

Mac comes with some tools by default. git is one that you want to make sure is up
to date so you can run the following in your terminal.

```shell
xcode-select --install
```

## Configuring git

Once you have installed git, configure the information that gets logged for each
of your commits by updating the default (global) credentials that git uses. (You
could overwrite these credentials temporarily per local repo. While that
shouldn't be necessary when working on App Academy projects, it is helpful to
know that it is an option.) You will also want to set the default branch to
`main`.

In your terminal (on Mac or WSL), run

```shell
git config --global user.name "Your Name"
git config --global user.email "Your Email"
git config --global init.defaultBranch main
```

Check that your name and email have been set up correctly by using the following commands:

```shell
git config user.name
git config user.email
```

You should see your name and email address returned. Repeat this step if there
are any errors.

## Configuring GitHub

As previously mentioned, GitHub provides a mechanism to share code with other
developers. Because of the nature of code, there needs to be a way to
authenticate to make sure that someone is authorized to fetch or contribute new
code.

Thankfully, git handles this authentication flow automatically. But for GitHub,
you can't use your GitHub account password. Instead, you can use a Personal
Access Token (PAT) or an SSH key as a password to authenticate to Github and
save it in a password manager of sorts so you don't have to use the token with
every command that requires authentication.

__If you have _never_ configured GitHub before, follow the instructions below to
set up your Secrets Manager and Personal Access Token. This is the recommended
approach for App Academy.__

If you are already using the SSH approach, then no need to follow the
instructions below! You can reference this [SSH article] instead for
troubleshooting your setup if needed.

### Secrets Manager

Before you get a PAT from Github and use it for auth - you should setup your
Secrets Manager.

#### Windows

WSL doesn't have a password manager by default in most distributions so you would
need to install one if you don't want your token saved in plain text or only
temporarily in memory. Thankfully, you can actually tell git to use Windows
Credential Manager. Just run the following command in WSL:

```shell
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/bin/git-credential-manager-core.exe"
```

You now have WSL trying to use the git-credential-manager-core to facilitate your
credentials management.

#### Mac

MacOS has a built in password/secret manager called keychain. You can tell git
to use keychain with the following line in your terminal:

```shell
git config --global credential.helper osxkeychain
```

### Personal Access Token
Once your secret manager is setup, you want to **restart your terminal/WSL
Shell**. Once restarted, you want to do two things. Generate a token from
Github, and use that as your authentication for a privileged command.

1. To get a new token, navigate to [Personal access tokens][PAT] in Github
   settings. You can navigate there yourself by going to `settings > Developer
   settings > Personal Access Tokens`.

2. Once here, click **Generate new token**.

3. Give your token a descriptive name. You can name it for the device you will
   use the token from. This way, each computer can have their own unique token
   and if you ever need to, you can revoke a token. You also want to use this
   menu to set when your token expires and give it the allowed permissions. For
   your purposes, you want to at least have all the repo permissions.

> Once you have your token ready to generate, you should try running a
> privileged command in git so you get a password prompt. Once you click
> **Generate token** at the bottom of the *new token form* you will only be able
> to see the token once.

4. Now that you have your token, you can use it when git prompts you for a
   password. If you are on Windows, you won't receive a password prompt but
   instead you will receive a pop-up that asks for you Personal Access Token.
   Because you previously configured your password/secret manager, your input
   will be saved for you. This way, you don't need to keep track of your PAT.

[git-win]: https://git-scm.com/download/win
[PAT]: https://github.com/settings/tokens
[SSH article]: https://hackmd.io/@AgDXdHgSSPKsJIhCxlaTuA/BJtNu88fF