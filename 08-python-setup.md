# Python Installation Instructions

Python is the second programming language you will use in this course.

> Note: We do not install Python using the installer from the python.org website
> in this course. If you have one installed, you should uninstall it before
> installing this version of python.

Currently the curriclum for this course is compatible with Python 3.9.

## Installing pyenv

The first thing you need is to install the Python version manager ([pyenv]).
This is similar to the `nvm` tool you used to install Node.JS, except it
controls what versions of python you use on your system.

To install pyenv we use the [pyenv-installer].

From the installation instructions on the [pyenv-installer] website, it says to
run the following command:

```shell
curl https://pyenv.run | bash
```

Unlike `nvm`, `pyenv` does not automatically add it's startup lines to your
shell startup file.

The files that you have to change will depend on which shell you are running
(you can check which shell you have by running `echo $SHELL`). Follow the
instructions to update the startup files associated with the shell that you are
running.

### If your shell is `zsh`

1. Open your `.zshrc` with the following command
```shell
code ~/.zshrc
```

2. Add the following lines.
```shell
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv init --path)"
```

### If your shell is `bash`

1. Open your `.bashrc` with the following command
```shell
code ~/.bashrc
```

2. Add the following lines.
```shell
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv init --path)"
```

To get your startup file to execute, restart your terminal.

## Installing dependencies on Windows and Ubuntu

*If you use macOS you can skip this step.*

For Windows and Ubuntu users you will need to install some extra dependencies
for python. (See here for more information about the prerequisites: [pyenv Prerequities])

First, run this command to update your apt repositories:

```shell
sudo apt update
```

Then, run this command to install the packages listed on the pyenv.

```shell
sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git
```

## Apple Silicon ONLY: Install openssl and readline

If you are using an M1 (silicon) mac, you need to install homebrew ARM versions of `openssl` and `readline`. All other users can skip this step.

```shell
brew install openssl readline
```

## Installing python itself

Now, you are ready to install python. You will be installing Python version
3.9.4.

Run this command to install python (you'll notice `pyenv` makes you put in the
_exact_ version instead of being able to just say `3.9` or `3`).

```shell
pyenv install 3.9.4
```

After some time, this should complete without any errors. It could take a while
since you are compiling python from source code.

Once this is finished, you also need to tell `pyenv` that this is our default
version of python using this command:

```shell
pyenv global 3.9.4
```

Ensure that these changes take effect by closing your terminal and opening
a new one. Then, verify your python is the correct version by typing:

```shell
python --version
python3 --version
```

Both of these commands should show 3.9.4.

## Pipenv

Another piece of software you will use in class is Pipenv.

```shell
pip install pipenv
```

After you have installed pipenv, add this line to your shell startup
file (either your `.bashrc` or your `.zshrc`) somewhere after
the  `eval "$(pyenv init --path)"`:

```shell
export PIPENV_VENV_IN_PROJECT=1
```

Congratulations! If you've completed all these steps you are ready to code in
Python!

[pyenv-installer]:https://github.com/pyenv/pyenv-installer
[pyenv]: https://github.com/pyenv/pyenv
[pyenv Prerequities]: https://github.com/pyenv/pyenv/wiki/Common-build-problems
