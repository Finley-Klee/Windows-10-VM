# Windows-10-VM
In this project I am beginning the set up of a home lab by creating a virtual instance of Windows 10 in Virtual Box on my personal laptop.

<h2>Description</h2>
As part of my Masterschool course I created a home lab using Virtual Box to participate in projects during our live sessions. This project details the creation of a virtual Windows 10 machine which will be used both as a "victim" machine for testing as well as for analysis. Since the Windows 10 machine will also be used for incident analysis, I am adding Sysmon and Mandiant's Flare-VM to this machine.

<h2>Utilities Used</h2>

- <b>Virtual Box</b> 
- <b>Windows Group Policy</b>
- <b>PowerShell</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>Project walk-through:</h2>

- <b>Creating a Windows 10 Virtual Machine</b>
<p>The first step in this project is to download a Windows 10 iso and install it on Virtual Box.</p>
<br>
<p align="center">I navigated to the Windows 10 Enterprise downloads page and downloaded the Windows 10 Enterprise 64-bit iso.<br/>
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/f70ef9c9-0960-4891-8c11-feccdf26a012" height="80%" width="80%" alt="the downloads page for Windows 10 Enterprise showing US English distributions in 32 and 64 bit versions."/>
  <br />
  <br />
  Next, I opened Virtual Box and under the Machine menu, I selected new to add a new virtual machine. I filled in the name field and navigated to the iso image in my host computer to import it to Virtual Box.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/c960798d-9eb3-4c8c-ade9-2f07f5117457" height="80%" width="80%" alt="the create virtual machine window of Virtual box is shown with fields such as name, folder, iso image, and edition."/>
  <br />
  <br />
  I allocated a small but reasonable amount of my host system's resources to the new virtual machine.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/2536d7c8-1096-4c3b-9d54-fdc6f51fec8c" height="80%" width="80%" alt="the hardware page of the create new machine window is shown with sliders to allocate the amount of base memory and processors."/>
   <br />
  <br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/3ce86dd9-7067-4869-80fe-63c33576de1e" height="80%" width="80%" alt="the virtual hard disk page of the create new machine window showing how much disk space to assign to the virtual machine for a virtual hard disk."/>
   <br />
  <br />
  Lastly, I launched the virtual machine and completed the installer process for windows.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/c3078c5a-26dd-427d-8082-0ccc7aea9e40" height="80%" width="80%" alt="Blue Windows setup window showing the progress of installing windows."/>
</p>
<br />
<br />
- <b>Preparing to install Sysmon and Flare</b>
<p>In order to download and intall Sysmon and Flare, I first had to temporarily disable auto-updates as well as tamper protections, anti-malware protections, and real time protection until the installation was finished.</p>
<br>
<p align="center">The first step was actually to enable bidirectional shared clipboard for the virtual machine, which I did in the advanced general settings of the machine in Virtual Box.<br/>
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/2bd03087-0d8e-4e38-847a-6e33aff63b7b" height="80%" width="80%" alt="the settings menu in Virtual box shows the advanced tab and next to the options for shared clipboard and drag 'n drop the bidirectional option is selected."/>
  <br />
  <br />
  Next, I opened Edit Group Policy<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/a030fc26-89e0-43cf-b073-5dd94234c7f2" height="80%" width="80%" alt="windows menu with edit group policy at the top."/>
  <br />
  <br />
  And navigated to the automatic updates policy under Computer Configuration - Administrative Templates - Windows Components - Windows Update<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/08d849ae-6ae9-4613-b290-4e4a39fe14b6" height="80%" width="80%" alt="local group policy editor window navigated to configure automatic updates in the selection."/>
   <br />
  <br />
  I configured automatic updates to disabled.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/8d4af3ed-a416-412f-a899-da8cf78c5c07" height="80%" width="80%" alt="automatic updates configuration window with the radio button disabled chosen."/>
   <br />
  <br />
 Next, I navigated to the Microsoft Defender Antivirus configurations to turn off Microsoft Defender Antivirus.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/a651c9ad-2436-403f-9775-b108e4b06eb4" height="80%" width="80%" alt="local group policy editor window with turn off microsoft defender antivirus selected."/>
  <br />
  <br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/a0756d5c-39e9-426e-9c56-cc9b4a433cd3" height="80%" width="80%" alt="turn off microsoft defender antivirus configuration window with the radio button for enabled selected."/>
   <br />
  <br />
 The last configuration I made was to disabled real time protection. This configuration is found under the Microsoft Defender Antivirus.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/54ea9b84-e103-4ee0-bc9c-554940e951bd" height="80%" width="80%" alt="local group policy editor window with turn off real time protection selected."/>
  <br />
  <br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/3f7aa8e7-05d1-4571-b1eb-b061ce11bf67" height="80%" width="80%" alt="turn off real time protection configuration window with the radio button for enabled selected."/>
  <br />
  <br />
  Finally, I took a snapshot of the Windows 10 machine using Virtual Box so that I could restore to this point before I have installed Flare if I want to.<br />
  <img src="https://github.com/Finley-Klee/Windows-10-VM/assets/171582741/d1e3e792-7adb-4c05-8934-2200178d594a" height="80%" width="80%" alt="the snapshots window for creating a new snapshot in virtual box showing snapshot name 'Pre-Flare Installation' and the description 'The state of the machine prior to installing Flare'."/>
</p>
