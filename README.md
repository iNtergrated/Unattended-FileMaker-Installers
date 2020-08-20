# Unattended FileMaker Installers #

> Updated for FileMaker Pro 19

FileMaker supports installing FileMaker with little to no human interaction, this guide will show you how to create them for Windows and macOS.

- [Claris FileMaker Network Setup Guide](https://help.claris.com/en/pro-network-install-setup-guide)

## macOS ##

1. Download the [Apple Remote Desktop script](https://www.claris.com/resources/documentation/docs/fmp_osx_deployment.zip)
2. Extract the downloaded file.
3. Open terminal, then type `cd `, and drag the extracted folder onto the terminal, and press enter.
4. Make the script executable: `chmod +x AppleRemoteDesktopDeployment.sh`
5. Create a folder inside the current directory: `mkdir FMP19`
6. Download and mount the latest FileMaker Pro disk image.
7. Download your FileMaker Pro installation certificate: `LicenseCert.fmcert`
8. Drag the `FileMaker Pro.app`, `Assisted Install.txt`, and `LicenseCert.fmcert` into the folder you created in step 5.
9. Open the `Assisted Install.txt` and edit, [About the personalization file](https://help.claris.com/en/pro-network-install-setup-guide/#personalization-file).
10. In terminal run the script: `./AppleRemoteDesktopDeployment.sh FMP19`
11. Finished, the newly generated pkg file will install FileMaker Pro.

## Windows ##

### Prerequisites ##
* [7-zip](https://www.7-zip.org/download.html)
* [7-Zip SFX Maker](http://sourceforge.net/projects/sfx-maker/)

1. Download and install 7-Zip: http://www.7-zip.org/
2. Download and install 7-Zip SFX Maker: http://sourceforge.net/projects/sfx-maker/
    - Optional, [ResourceHacker](http://www.angusj.com/resourcehacker/), download the [zip install](http://www.angusj.com/resourcehacker/resource_hacker.zip).
    - Double-click to open zip, and drag `ResourceHacker` to `C:\Program Files (x86)\7-Zip SFX Maker`.
    - Rename `ResourceHacker` to `ResHacker`.
3. Extract the FileMaker Installer/Archive provided by FileMaker, Inc.
	* Right-click on the FileMaker Installer (e.g. fmp_19.0.1.116_x64.exe)
	* Choose 7-Zip -> Extract Here
4. Open the newly created folder (e.g. FileMaker Pro 19.0.1.116_x64 )
5. Edit "Files/Assisted Install.txt", [About the personalization file](https://help.claris.com/en/pro-network-install-setup-guide/#personalization-file).
6. Go to the previous folder, select the setup files (e.g. Extras, Files and Setup ), right-click, and choose 7-Zip -> Add to Archive.

    ![Create Archive](https://cdn.intergrated.net/git.intergrated.net/unattended-file-maker-installers/01-create-archive.png)

7. In the configuration screen, make sure the `Compression method` is set to `LZMA`, then click `OK`.

    ![Configure Archive](https://cdn.intergrated.net/git.intergrated.net/unattended-file-maker-installers/02-configure-archive.png)

8. Open 7-Zip SFX Maker (right-click, Run as administrator).
9. *(optional)* Click "Load Settings..." and select the example config, "Example Config".
	* [Download Example Configuration](FMP%207-Zip%20SFX%20Maker%20Config.xml)
	* [Download Silent Install Example Configuration](FMP%207-Zip%20SFX%20Maker%20Config%20-%20Silent.xml)
10. Go to files tab, click "+" to and select the archive you created in step 7.
11. Go to the dialog tab.
    1. Go to the *General* tab.
        - Enter a title, e.g. `FileMaker Pro 19.0.1.116`
        - Change any other settings as needed.
    2. Go to the *Begin prompt* tab.
        - Check *Begin prompt* box
        - Enter a description, e.g. `Install FileMaker Pro 19?`
    3. Go to the *ExtractPath* tab.
        - Uncheck `Allow user to change path`
    4. Go to the `Progress` tab.
        - Change as needed.
    5. Change any desired settings on the *Finish message* and *Cancel prompt* tabs.
12. Go to the *Tasks* tab.
    1. Click the `+`
    2. Select `Run a program`.
    3. Click `OK`.
    4. In the *Run Program* Dialog, enter the following:
        - Program: `%%T\setup.exe`
        - Arguments: `/qb+ /norestart`
    5. Click `OK`.

12. Go to the *Metadata* tab, and make any desired changes.
    > This does not appear to work.
13. Once you have customized the configuration, you may want to save a copy by clicking the "Save settings..." button.
13. Click "Make SFX" to build your Self-Extracting installer.