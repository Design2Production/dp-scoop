# DP New Installation for Indoor - Single PC

# Pre Installation
Ensure the Ethernet connection to the switch (connected to the internet) is made prior to installation, otherwise the automatic network configuration will throw an exception and abort the installation.

    1. Connect the longer Ethernet cable from the PCs to the swith to the left most port (when looking from the front of the PC)

# DeviceProxy Installation

1. Start Powershell as Administrator
<pre>
    1. Press the **Windows** key
    2. Type Powershell
    3. Right-Click on **Windows Powershell*** and select **"Run As Administrator"**
    4. Click on **Yes** when asked for permission
</pre>

2. Download the install script for a NEW installation
<pre>
Invoke-WebRequest -Uri https://design2production.github.io/dp-scoop/NewInstallDeviceProxy.ps1 -OutFile NewInstallDeviceProxy.ps1
</pre>

> If the installation script fails with:
>
> ***Invoke-WebRequest : The request was aborted: Could not create SSL/TLS secure channel***
> then enter the following command and retry the Invoke-Web-Request command
> <pre>
> [Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls"
> </pre>
> If the installation script can't run then enter the following command to allow Powershell to execute local scripts.
> <pre>
> Set-Executionpolicy remotesigned -scope currentuser -Force 
> </pre>

3. Run the install script using the ***Unique-Device-Id*** for the unit:

<pre>.\NewInstallDeviceProxy.ps1 Production singlePC Unique-Device-Id DPEMS-V1_DBV2</pre>

The arguments are as follows:
<pre>
      Production = which server to use: Staging | Production
        singlePc = InstallationType: singlePC|dualPC
Unique-Device-Id = Surevision Unique Device Id for this unit
   DPEMS-V1_DBV3 = DPEMS Hardware for Indoor Units
        </pre>

> Ensure there are no errors reported during installation - it can take a long time to install, particularly on machines with slow or intermittant internet