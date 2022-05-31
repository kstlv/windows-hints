# Windows Hints

Here you will find useful commands, tutorials, guides, tips and other stuff to make the process of using Windows more comfortable.

## Registry

`.reg` files are located in the `reg` folder. Run the file you need.

## Useful commands

Commands that can only be executed in `powershell.exe` are marked. The rest must work in `cmd.exe`.

Some of the commands require administrator rights.

### Info about PC components

You can find the OS version, motherboard model name, processor, amount of RAM, and more.

```cmd
msinfo32
```

### Check system files

Restores system files if problems are found.

```cmd
SFC /scannow
```

### File MD5 checksum

`PowerShell`

When downloading or transferring any file, especially a large one, there is always a chance that it will be damaged. And the easiest way to find out if a file is intact is to compare its checksum on your computer and on the resource from where you downloaded this file.

Get MD5 checksum of the file `C:\foo.txt`:

```powershell
Get-FileHash C:\foo.txt -Algorithm MD5 | Format-List
```

### Disable UAC notifications

> Don't do this if you don't want to risk your computer's security!

If you are tired of pop-ups warning about the safety of performing an action, then you can turn them off.

1. `UserAccountControlSettings` in cmd or powershell.
2. Set "Never notify"

### Delete/remove/uninstall UWP apps

`PowerShell`

Decide what you need to remove. Run one or more commands:

```powershell
Get-AppxPackage -AllUsers *3d* | Remove-AppxPackage
Get-AppxPackage -AllUsers *camera* | Remove-AppxPackage
Get-AppxPackage -AllUsers *communi* | Remove-AppxPackage
Get-AppxPackage -AllUsers *bing* | Remove-AppxPackage
Get-AppxPackage -AllUsers *zune* | Remove-AppxPackage
Get-AppxPackage -AllUsers *phone* | Remove-AppxPackage
Get-AppxPackage -AllUsers *photo* | Remove-AppxPackage
Get-AppxPackage -AllUsers *solit* | Remove-AppxPackage
Get-AppxPackage -AllUsers *skype* | Remove-AppxPackage
Get-AppxPackage -AllUsers *maps* | Remove-AppxPackage
Get-AppxPackage -AllUsers *3dbuilder* | Remove-AppxPackage
Get-AppxPackage -AllUsers *windowscommunicationsapps* | Remove-AppxPackage
Get-AppxPackage -AllUsers *windowscamera* | Remove-AppxPackage
Get-AppxPackage -AllUsers *officehub* | Remove-AppxPackage
Get-AppxPackage -AllUsers *skypeapp* | Remove-AppxPackage
Get-AppxPackage -AllUsers *getstarted* | Remove-AppxPackage
Get-AppxPackage -AllUsers *zunemusic* | Remove-AppxPackage
Get-AppxPackage -AllUsers *Microsoft.Messaging* | Remove-AppxPackage
```

## Disabling telemetry

The methods described below may not be as effective and are no longer relevant.

### Blocking in hosts file

Add to `%SystemRoot%\system32\drivers\etc\hosts`:

```
127.0.0.1 vortex.data.microsoft.com
127.0.0.1 vortex-win.data.microsoft.com
127.0.0.1 telecommand.telemetry.microsoft.com
127.0.0.1 telecommand.telemetry.microsoft.com.nsatc.net
127.0.0.1 oca.telemetry.microsoft.com
127.0.0.1 oca.telemetry.microsoft.com.nsatc.net
127.0.0.1 sqm.telemetry.microsoft.com
127.0.0.1 sqm.telemetry.microsoft.com.nsatc.net
127.0.0.1 watson.telemetry.microsoft.com
127.0.0.1 watson.telemetry.microsoft.com.nsatc.net
127.0.0.1 redir.metaservices.microsoft.com
127.0.0.1 choice.microsoft.com
127.0.0.1 choice.microsoft.com.nsatc.net
127.0.0.1 df.telemetry.microsoft.com
127.0.0.1 reports.wes.df.telemetry.microsoft.com
127.0.0.1 wes.df.telemetry.microsoft.com
127.0.0.1 services.wes.df.telemetry.microsoft.com
127.0.0.1 sqm.df.telemetry.microsoft.com
127.0.0.1 telemetry.microsoft.com
127.0.0.1 watson.ppe.telemetry.microsoft.com
127.0.0.1 telemetry.appex.bing.net
127.0.0.1 telemetry.urs.microsoft.com
127.0.0.1 telemetry.appex.bing.net:443
127.0.0.1 settings-sandbox.data.microsoft.com
127.0.0.1 vortex-sandbox.data.microsoft.com
127.0.0.1 survey.watson.microsoft.com
127.0.0.1 watson.live.com
127.0.0.1 watson.microsoft.com
127.0.0.1 statsfe2.ws.microsoft.com
127.0.0.1 corpext.msitadfs.glbdns2.microsoft.com
127.0.0.1 compatexchange.cloudapp.net
127.0.0.1 cs1.wpc.v0cdn.net
127.0.0.1 a-0001.a-msedge.net
127.0.0.1 statsfe2.update.microsoft.com.akadns.net
127.0.0.1 sls.update.microsoft.com.akadns.net
127.0.0.1 fe2.update.microsoft.com.akadns.net
127.0.0.1 65.55.108.23
127.0.0.1 65.39.117.230
127.0.0.1 23.218.212.69
127.0.0.1 134.170.30.202
127.0.0.1 137.116.81.24
127.0.0.1 diagnostics.support.microsoft.com
127.0.0.1 corp.sts.microsoft.com
127.0.0.1 statsfe1.ws.microsoft.com
127.0.0.1 pre.footprintpredict.com
127.0.0.1 204.79.197.200
127.0.0.1 23.218.212.69
127.0.0.1 i1.services.social.microsoft.com
127.0.0.1 i1.services.social.microsoft.com.nsatc.net
127.0.0.1 feedback.windows.com
127.0.0.1 feedback.microsoft-hohm.com
127.0.0.1 feedback.search.microsoft.com
```

### Removing the auto logger

Run the following commands in cmd:

```cmd
sc delete DiagTrack
sc delete dmwappushservice
echo "" > C:\ProgramData\Microsoft\Diagnosis\ETLLogs\AutoLogger\AutoLogger-Diagtrack-Listener.etl
```
