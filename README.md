# Adding Framebot to your Discord Server

### Overview
First you will make a discord bot and invite it to your server. Then, you will download the framebot code and run it on some computer (your own, or some remote server). By giving the framebot your discord bot's credentials in the form of a token, it will be able to listen to discord messages and respond on your bot's behalf.

### Prerequisites
- [Make a discord bot and acquire the token](https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token)
- [Install Python](https://www.python.org/downloads/) on your computer

## Get the Framebot Source Code (or write your own)
The most commonly used framebot is located [here](https://github.com/BKNR/mokujin). If you don't have a github account already set up, the easiest way to acquire the code is to hit the green **Code** button, then click **Download as ZIP** on the popup that appears. Then, unzip the files.

## Give the Framebot Access to Your Discord Bot
The framebot is instructed to look for a specific file on startup. In this file it expects to find your token which it can send to Discord to prove that it has permission to post on your server. The bot expects the following: the file must be named `token.txt` exactly, and its contents must be nothing but your token, which looks something like this `NzFJfew8fSkhje3F3fsFoef.ZJ3jdfLkwe90sfFZOnzcpwod89`. Further, the file must be located in the same directory as the bot's code -- it must be a sibling file to `mojukin.py`.  So, create a new text file in the same folder as the framebot's code, paste your token, and save the file.

**IMPORTANT: you should NEVER give your bot token to anybody you do not trust, and especially never publish it in a public location, such as a Git repo. The token gives full access to your bot account, and a malicious actor could use it to hijack the bot (ranging from the irritating – such as leaving all your servers, and breaking your bridge – to the much more serious – such a spamming unfavorable links or deleting messages and channels in servers where it has moderator permissions). Keep your token secret!**

## Activate Framebot
With the source code and permissions ready to go, we can now start up the bot. Depending on your experience, follow the instructions outlined in one of the sections below.

### If you are experienced with the command line

Install the required dependency `discord.py` with your preferred package manager. For example: `python -m pip install discord.py`. Navigate to the directory that contains `mokujin.py` and start the script with python: `python mokujin.py`. You should see a "success message" like `Logged in as <bot_name>`. The frame bot is now activated for your server. By default, the bot will only respond if the message was sent in an approved channel. You can modify the `CHANNELS` item in `config.py` to include the names of any channels in your server that the bot should be active in.

### If you are not experienced with the command line

*NOTE*: This is written assuming you are on Windows 10.

We will now instruct python to run our bot. We are going to have to use our computer's *terminal*, which is a text-based program that lets us interact with our computer directly. The recommended terminal program is called `PowerShell` and is likely already installed on your system. Open PowerShell and you will see a blue window with a text prompt. Our goal is to use PowerShell to navigate through our computer's filesystem and find the Framebot files we downloaded earlier, then to tell our computer to use python to run the framebot files.

To ensure we have python installed properly, enter this command: `python --version`. You should see something like this: `Python 3.8.6`. If not, ensure that you downloaded and installed python (check #Prerequisites above). If you did, you may have to [add Python to your computer's PATH variable](https://thetechhacker.com/2021/01/23/add-python-path-to-windows-10/).  Note that the framebot requires Python 3.6 or higher.

The framebot relies on an external library (or "package") called `discord.py` being available on your computer. To make this code available, you can use python's built-in package manager `pip`. Run the following command in your terminal to install the package: `python -m pip install discord.py`. You should see a bunch of messages that indicate that this external program is now available to python.

Next we will navigate to the bot code inside the terminal. Enter `cd` in the terminal to see your terminal's current location. Enter `ls` to see all files present at the terminal's current location. Based on the output of `ls`, determine which folder you need to navigate to (by default, the bot's files were probably placed into `Downloads`), and type `cd <folder_name>` (ex: `cd Downloads`). Use `ls` and `cd` until you see `mokujin.py` in your current directory.

Tell python to activate the bot: `python mokujin.py`. The bot will start running. You should see a "success message" like `Logged in as <bot_name>`. The frame bot is now activated for your server. Your terminal no longer accepts input, as it is busy running the bot. The bot is active only for as long as your terminal is open, and the bot will de-activate once you close the terminal or power off your computer.

Note that the bot is configured, by default, to only respond to messages sent in an approved channel. You can open the file `config.py` in Notepad or any other text editor and modify the `CHANNELS` item to include the names of any channels you would like the bot to be active in. For example, if your server includes a channel called "frame-data", you can edit the line to appear as so:

```
CHANNELS = ["tekken", "raamikysely", "tekken-frames", "frame-data"]
```

## Hosting The Bot
If you want your bot to always be active, not just when you have it running on your own computer, you will need to activate the bot on a computer that is always available. If you want, you can just leave your computer on 24/7. But since that is inconvenient, it might be better to rent someone else's computer and tell the bot to run there. There are many such services, and they are all made very affordable (usually about 5 USD per month). Some services include those offered by [Linode](https://cloud.linode.com/linodes),  [AWS](https://aws.amazon.com/) (using their [EC2](https://aws.amazon.com/ec2/) service), Google Cloud, Microsoft Azure, and many others. All of these services will require that you sign up with a credit card.

(NOTE: The following paragraph is light on details)

Once you activate your remote server, you can remotely access it via the terminal, transfer the bot files and your token to it, then activate the bot, and terminate your remote connection to the server. The bot is now running "in the cloud" and will always be available.

