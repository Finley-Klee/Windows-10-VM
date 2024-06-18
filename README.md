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
  Step Two: <br />

  <img src="" height="80%" width="80%" alt="image two"/>
  <br />
  <br />
  Step Three: <br />
  <img src="" height="80%" width="80%" alt="image three"/>
   <br />
  <br />
  Step Four: <br />
  <img src="" height="80%" width="80%" alt="image four"/>
   <br />
  <br />
  Step Five: <br />
  <img src="" height="80%" width="80%" alt="image five"/>
</p>

