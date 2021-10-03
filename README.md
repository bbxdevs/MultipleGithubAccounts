# Multiple Github Accounts on one PC with SSH access to repos

## Steps:

- Generate an SSH-key

``$ ssh-keygen -t rsa -C "john@doe.com"``

- follow the prompts and decide a name, e.g. *id_rsa_doe_company*.

- Copy the SSH public-key to GitHub from 

``~/.ssh/id_rsa_doe_company.pub``

- and tell ssh about the key:

``ssh-add ~/.ssh/id_rsa_doe_company``

- Create or Edit the config file in ~/.ssh with the following contents:

``Host github-doe-company
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_doe_company``

- Add your remote: 

``git remote add origin git@github-doe-company:username/repo.git``

- or change using 

``git remote set-url origin git@github-doe-company:username/repo.git``

## Note

This short guide it's not my original content and follows the indications explained on this [StackOverflow](https://stackoverflow.com/questions/3860112/multiple-github-accounts-on-the-same-computer/3860139#3860139) Post.
