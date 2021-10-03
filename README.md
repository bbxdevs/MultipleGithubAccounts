# Multiple Github Accounts on one PC with SSH access to repos

## Disclosure:

We assume that you currently have a github profile with repos on your machine, and now, you need to add a different profile with new repos (maybe from your job). Also, we have updated the original code lines to mimic Github's official documentation.

## Steps:

- Generate a new SSH-key [(Official documentation)](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)

```
$ ssh-keygen -t ed25519 -C "john@doe.com"
```

- Follow the prompts and decide a name, e.g. *id_rsa_doe_company*.

- Add the new key to the SSH Agent [(Official documentation)](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)

```
$ ssh-add ~/.ssh/id_rsa_doe_company
```

- Copy the SSH public-key like this, and then save it on Github [(Official documentation)](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

```
$ cat ~/.ssh/id_rsa_doe_company.pub
```

- Create or Edit the config file in ***~/.ssh/config*** with the following contents:

```
Host github-doe-company
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_doe_company
```

**That's it!** Your PC is ready to handle several repos from several github profiles. You can now clone or add repos using the correct *Host* name from your ***~/.ssh/config*** file.

- Add your remote: 

```
$ git remote add origin git@github-doe-company:username/repo.git
```

- or change one using 

```
$ git remote set-url origin git@github-doe-company:username/repo.git
```

## Note

This short guide it's not my original content and follows the indications explained on this [StackOverflow](https://stackoverflow.com/questions/3860112/multiple-github-accounts-on-the-same-computer/3860139#3860139) Post.
