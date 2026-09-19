> **Notice:** You have to run the `run_shell` file for testing first before running the `Launcher.exe` file. Make sure that you follow these instructions step by step. The default password is `123`.

## Setup Instructions

### Step 1: Change All Sensitive Variables
The variables include passwords, face vectors, and API keys.
You will need to change them in the `pc-lock-system` folder.
You can take your face vectors in index.html file(which is not in the `pc-lock-system` folder or in `Monitering_system` folder), you have to do it 5 times to take 5 vectors to replace into the MASTER_FACE_VECTORS in `pc-lock-system`.
You should use AI to compress 5 vectors in to 1 line to ensure that the system works, also, if you do not have knowledge about coding, you should ask IT specialist or AI(It is helpful because it can search easily on the internet to provide correct guild to you).
> **Notice:** The default euclid distance(which is the alignment between the user face and the vector) is 0.33, if you think that this is too strict, you can increase it to standard number: 0.42.
### Step 2: Add Environment Variables to Vercel
Add the variables in the `Monitoring_system` folder.
The variables are:
* `CLOUDINARY_API_SECRET`
* `CLOUDINARY_API_KEY`
* `CLOUDINARY_CLOUD_NAME`
* `MASTER_PASSWORD`
* `MASTER_FACE_VECTORS`
* `FIREBASE_PRIVATE_KEY`
* `FIREBASE_CLIENT_EMAIL`
* `FIREBASE_PROJECT_ID`

The command to paste into the terminal to add variables to Vercel:
vercel env add "variable_name"

### Step 3: Testing
You must run the `run_shell` file because it is designed for testing cases. It allows you to open the command prompt (cmd) to stop the system if errors occur.

> **Notice:** While setting up this system, please do not shut down your computer; otherwise, when you turn it on next time, the system will lock your PC (you can use the password to unlock, but this step ensures your safety).

### Step 4: Configure Your Device
* **First:** Turn on device encryption in Windows settings.
* **Second:** Paste these codes into the command prompt (as administrator):
  reg add "HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Minimal" /v "Disabled" /t REG_SZ /d "1" /f
  reg add "HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Network" /v "Disabled" /t REG_SZ /d "1" /f
  bcdedit /set {globalsettings} advancedoptions false
  bcdedit /set {current} bootstatuspolicy ignoreallfailures

  > **Notice:** The function of this code is to prevent attackers from entering safe mode. If they can access safe mode, they could delete the system files.
* **Third:** Put the `pc-lock-system` folder into the whitelist of Windows Security.
* **Fourth:** Grant administrator permissions to the `Launcher.exe` file.
* **Fifth:** Remove all other permissions that can access the `.env` file, because other background systems could read your sensitive variables if you skip this step.
* **Finally:** Set up a BIOS password. Restart your computer and press `F2` consecutively to open the BIOS control panel. At the bottom right corner, find the area to set up a password, and make sure to set up the **administrator password**, not the user password.

You have finished all steps. Have a wonderful day!