# Windows Hints

Here you will find useful commands, tutorials, guides, tips and other stuff to make the process of using Windows more comfortable.

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
