### Overview
An automated Github setup tool that will:
1. Create your account
2. Setup your SSH key
3. Create your first repo
4. Clone your first repo to local
5. Create your first file
6. Add, commit, and push your first file to git

### Installation

GHSU is a PyPi package installable via pip. 

First ensure you have python3 installed via:
```sh
sudo apt install python3.6
```

Then install the package installer for Python, pip, via:

```sh
sudo apt-get install python3-pip
```

Finally, install GHSU using pip:

```sh
pip install ghsu
```

GHSU employs a software automation library, selenium, which makes calls to Google Chrome. If you don't have Chrome installed, join the rest of the 21st century and please install it.

### Usage 

In the terminal, run:

```sh
ghsu
```

And you should be prompted for a email, password, and username. Make sure the password is secure (i.e. containing numbers, letters (upper-/lowercase), and special characters).

```sh
Enter your email:
<emailusername>@<server>.<domain>

Enter your password:
<password>

Enter your username:
<username>
```

The script should open a chrome window and begin setup. Eventually, the script should pause and you should be prompted to complete a captcha.

After completion, the script should setup your SSH key, create and clone your first repo, pull that repo to local, create a test file, and push that file to Github.

_If you have already set up a Github account, but have not set your SSH key, run_:

```sh
ghsussh
```

_If you have already set up a Github account and SSH key, but have not yet created, cloned, and pushed to a repo, run_:

```sh
ghsurepo
```

### What the frick is the script actually doing?

1. Creates your account
2. Sets up your SSH key
  1. SSH keys are extremely valuable, as they provide git with a means to establish a secure connection such that password entry is not needed for pushing/pulling code. Your SSH key is set up by running "ssh-keygen -t ed25519 -C "your_email@example.com"" inside your terminal. This key is then copied and pasted into Github
3. Navigates to "https://github.com/settings/keys" and copies the key generated by ssh-keygen into Github
  1. After saving the key, we're now able to pull/push code via SSH (devoid of passwords)
4. Creates a repo and copies the SSH link
5. Clones that repo via "git clone <ssh-repo-link>"
6. Navigates to the newly cloned repo and:
  1. Creates a file
  2. Populates it with some code
  3. Stages that code for pushing with "git add <file>"
  4. Commits the changes with "git commit -m "<comment>"
  5. Pushes that code via "git push <file>"
