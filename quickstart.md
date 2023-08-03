# Quick start

## Prerequisites

To get started, you will need to have
- [a google account](quickstart?id=setting-up-a-google-account)
- [a github account](quickstart?id=setting-up-a-github-account). *This is optional and its only for more technical users*

If you already have a google account and would like to jump straight in, you can skip these steps and go to [Running the Code](running-the-code)

## Setting up a google account

Although this step is not about setting up gmail, if you already have a gmail account, you are good to go and you can safely skip this step.

We will guide through the rest of the step through a way that you can use to skip google phone verification if all goes well.

To set up a google acccount without being asked for a verification phone number (which will not be accepted after you open `too many` accounts with it), you need to first have a private email such as privateemail@cseco.co.ke. Setting up the mail server is beyond the scope of these instructions.

### Creating a new account on mail-in-a-box server

If your emails are hosted using a mail-in-a-box server, you can easily create a new email using the following command to make an API call:

```bash
curl -s -X POST "https://{domain}/admin/mail/users/add" -d "email={email}" -d "password={password}" -u "{adminEmail}:{adminPassword}"
```
This bash command can be run in [this noteboook](https://colab.research.google.com/github/adventHymnals/resources/blob/master/Bash_Tools.ipynb). Or you can create a new notebook to run it (this is the safer way), if you do not have access to a linux machine.

Or you can the more easily use your admin interface to create the email.

With your private email at hand, you can now create an google account either:
- Directly (you will need a phone number for verification)
- From an invite from google workspace

#### Creating Directly
Armed with your new email account, create a youtube account using that email address. For this go to youtube, or any other Google service like google drive, etc, and click either `sign in` or if you are already logged in to Google, click your profile picture, then `switch account`, then `add account`. You should end up on the following page.

![New Account](_images/google/new_account.png 'New Account')


Click on `Create Account` and select `For work or my Business`

![New Account](_images/google/new_account_1.png 'New Account')

Create the account using your private email account for your domain.


#### Creating From Workspace Invite
Alternatively, you can create the google account through an invite from a google workspace account. With this, you will skip the step of mobile phone verification. A free workspace account can be created [here](https://workspace.google.com/essentials/). However, if you create from a workspace invite, you will not have access to `google colab`, if using free(enterprise) workspace. So you will have to remove the email from the workspace after it has successfully been created and registered as a team member of the google workspace. Note that a workspace can only have emails of a single domain. You may in some instances skip the phone verification part after the account is removed from the workspace. 


## Setting up a github account

This step is optional and only required if you'd like to host you resume on a page like [this one](https://surgbc.github.io/vue-resume).

This is pretty much straight forward. Go to [GitHub](https://github.com/) and create an account.

### Forking the Repo
Once you have your github account and you are logged in, open [this page](https://github.com/csymapp/vue-resume/fork) to start forking vue-resume.

![Forking](_images/vue-resume-fork.PNG 'Fork')

Select the owner and click to uncheck the `Copy the Master Branch only` checkbox.

Once the forking process is complete, click on `Actions` menu at the top bar (third item from the left). On the actions page, select `I understand my workflows, go ahead and enable them` to enable the workflow.

On the left, under `Actions` click on the workflow called `Deploy Nuxt Site to Pages`. Once the workflow has been shown on the page, click on `Run workflow` and `Run workflow` leaving the selected branch as `master`. You first resume site is now being built. You can check on the progress by clicking on the `Actions` menu again. This process will take longer than is desired (about 5 minutes). We are working to optimize the code to have it build faster.

![Workflow Section](_images/workflow_selection.PNG 'Selection')

### Setting up Github Pages
On the github page, click on `settings`. Then on the left side-menu click on `Pages`. Under source select `Deploy from Branch`, then under branch select `gh-pages` and `Save`

![Enable pages](_images/enable_pages.PNG 'Pages')

Click on `Actions` again in the top menu and you should see an action called `pages build and deployment` running. Once it is done, click on it to open it, you should be able to see the url of your resume. It should be in the form `https://{your_github_username}.github.io/vue-resume`. This resume has been created using the data in resume-data.json. You can edit this file with your own data and the resume will be automatically updated. If you don't want to manually edit this file, you can proceed on to the next step.

![Resume Url](_images/resume_url.PNG 'Resume')

## Generating an ssh key
To generate an ssh key run following commands in your computer terminal. Or use [this colab notebook](https://colab.research.google.com/github/adventHymnals/resources/blob/master/Bash_Tools.ipynb). Check the section under `Generate SSH key`.

1. 
` ssh-keygen -t ed25519 -C "your_email@example.com"`

(the type of key ed25519 is recommended by the [GitHub documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key).)

2. ssh-keygen will ask for a file path: *Enter file in which to save the key:* We suggest that you run this in colab so that you can leave it as `id_rsa`

3. Enter a paraphrase

4. Use the paraphrase as the password to compress id_rsa into ssh.zip. ssh.zip has inside it a directory called `ssh` which contains the keys.

5. Copy the contents of id_rsa.pub using `cat id_rsa.pub`

## Setting up ssh keys in GitHub

If you have reached this part, you are almost done. The next step step is to set up ssh keys in github. For this, follow these steps:

1. Go to github.com (you should be already logged in already.) Click on your profile picture (at the top right corner), and select `Your repositories`

![ssh key set up](_images/github/your_repos.png 'ssh key set up')

2. At the top, click on `repositories`. The open the repo you forked in the previous steps (vue-resume).

![ssh key set up](_images/github/select_repos.png 'ssh key set up')

3. Next, click on `settings`.

![ssh key set up](_images/github/ssh_key_1.png 'ssh key set up')

4. Next, on the left sidebar find `Deploy Keys` and click on it. Then click on `Add Deploy Key`

![ssh key set up](_images/github/ssh_key_2.png 'ssh key set up')

5. In the form that comes up enter `Website Key` or any other name as the title, then click on `Allow write access` to enable it.

![ssh key set up](_images/github/ssh_key_3.png 'ssh key set up')

6. Paste inside `key` and submit the form the key you copied from the colab script (the public key) in the previous step.
