# Table of Contents

- [Original Authors Notes](#original-authors-notes)
- [Authors Known Issues](#authors-known-issues)

## Atomic Documentation
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
  - [1. Set Up Dependencies](#set-up-dependencies)
  - [2. Clone the Repository](#clone-the-repository)
  - [3. Configure Google Cloud API](#configure-google-cloud-api)
  - [4. Configure the Bot](#configure-the-bot)
  - [5. Run the Bot](#run-the-bot)
- [Additional Notes](#additional-notes)
- [Troubleshooting](#troubleshooting)
- [License](#license)

# eZwizard3-bot
<a name="original-authors-notes"></a>
A discord bot that connects to your jb ps4 (9.00 only atm) to allow other people to do save things with it

this project is activily being worked on by Zhaxxy and is very passionate about it, please feel free to ask for any suggestions, reporting any bugs, or even making your own changes and make a pull request, Zhaxxy will be sure to respond!

# Known issues
<a name="authors-known-issues"></a>

## RuntimeError: coroutine ignored GeneratorExit

If theres more then one connection to the ps4 at a time it is very likley that the bot will fail and get `RuntimeError: coroutine ignored GeneratorExit` so make sure theres nothing else connected to the ps4 network. That error also ignores any context managers so if it happens the bot will likley be stuck and ps4 need reboot, PLEASE ANYONE TELL ME HOW TO FIX THIS

bot can sometimes get stuck at some part which involves the mounted_saves_at_once semaphore, which will cause it to get stuck on other commands, which will start spamming chats with tick tocks eventually, my suspicon is that it has something to do with the discord api libary interactions.py which im using I seem to have fixed bot of the above using mutiple messures, but it could still happen i just havent seen it happen after my fixes, even with external ftp clients attached

## SCE_SAVE_DATA_ERROR_BROKEN sometimes on saves
this is likley because of a new gold hen version, please use known working version `v2.4b17.3`



<a name="features"></a>
## Features
- PS4 save data management and patching
- Google Drive integration for large save file storage
- PS4 FTP connection and firmware checks
- Automated Discord commands for interacting with PS4 saves
- Java-based support for additional game-related encryption and decryption operations


## Requirements
<a name="requirements"></a>
- Python 3.12
- Java Development Kit (JDK) 17 (build 17.0.8+7-44) \n Specifically, JDK 17.0.8+7-44 from July 2023 was needed, as newer versions may not be compatible.
- lbptools.py for interacting with the PS4 save data
- 7Zip 

# Installation
<a name="installation"></a>

## 1. Set Up Dependencies
<a name="set-up-dependencies"></a>
### Java Installation
Go to the Java JDK Archive.
Scroll to JDK 17.0.8+7-44 (from July 2023).
Download and install the version specific to your OS.

### lbptools.py Setup
Clone the lbptools.py repository:
```
git clone https://github.com/Zhaxxy/lbptools.py.git
```

Follow the installation instructions on the lbptools.py GitHub page to install any required dependencies and build the tool if necessary.


## 2. Clone the Repository
<a name="clone-the-repository"></a>
To ensure all required submodules are included, use the following:

```
git clone https://github.com/YourUsername/PSDiscordBot2.git --recurse-submodules
cd PSDiscordBot2
git submodule update --init --recursive
```

## 3. Configure Google Cloud API
<a name="configure-google-cloud-api"></a>
The bot uses Google Drive for storage of large save files. Follow these steps to set up your Google Cloud project and configure it for Drive API access:

Go to Google Cloud Console.
Create a new project (or select an existing one).
In the API Library, search for and enable the Google Drive API.
Set up OAuth 2.0 credentials:
Go to Credentials and click Create Credentials > OAuth client ID.
Configure the consent screen and download the credentials.json file.
Place credentials.json in the project directory (PSDiscordBot2/credentials.json).

## 4. Configure the Bot
<a name="configure-the-bot"></a>
Open the config.json file and update the following fields:

Google Cloud API user ID: Confirm your Google API credentials.
Discord API Token: Obtain a token from the Discord Developer Portal.
PS4 User ID: This must match the PS4 profile associated with the save files.
```
{
  "user_id": "YourPS4UserID",
  "discord_token": "YourDiscordToken",
  "google_drive_folder": "ezwizardtwo_saves"
}
```

## 5. Run the Bot
<a name="run-the-bot"></a>
With all dependencies and configurations complete, you’re ready to launch:
```
python main.py
```

### Additional Notes
<a name="additional-notes"></a>
- Java Version: Using the specific version, JDK 17 (build 17.0.8+7-44), proved necessary. Downloading newer versions caused compatibility issues for me.
- lbptools.py: Follow the repository’s setup instructions for full compatibility with this bot’s requirements.
- Google Drive Folder: The bot automatically checks and creates the folder ezwizardtwo_saves on Google Drive if it doesn’t already exist.

# Troubleshooting
<a name="troubleshooting"></a>
If you encounter any issues, consider the following:

- Module Errors: Ensure all modules and submodules are installed properly.
- Invalid Login Errors: Double-check your PS4 User ID in config.json.
- FTP and API Connectivity: Confirm the PS4 firmware and FTP setup allow communication with the bot.
- Java Compatibility: Verify that the correct JDK version is installed, as incompatible versions may prevent the bot from functioning correctly.

# License
<a name="license"></a>
This project is licensed under the MIT License.
