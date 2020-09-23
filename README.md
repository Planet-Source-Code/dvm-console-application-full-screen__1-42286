<div align="center">

## console application full screen


</div>

### Description

get your vbscript console applications running under cscript using the stdin & stdout objects for input running full-screen. and get the fore and background collor set to the color you like
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[DVM](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/dvm.md)
**Level**          |Beginner
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB Script
**Category**       |[Registry](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/registry__1-36.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/dvm-console-application-full-screen__1-42286/archive/master.zip)





### Source Code

```
option explicit
dim oShell: set oShell = CreateObject("WScript.Shell")
' asume it started tweaked
dim bTweaked: bTweaked = true
' is it tweaked?
if wscript.arguments.count = 0 then
 bTweaked = false
elseif not wscript.arguments(0) = "tweaked" then
 bTweaked = false
end if
' if not, let's tweak it
if not bTweaked then
 dim kFullScreen, kScreenColors
 kFullScreen = oShell.regRead("HKCU\Console\FullScreen")
 kScreenColors = oShell.regRead("HKCU\Console\ScreenColors")
 oShell.regwrite "HKCU\Console\FullScreen", 1, "REG_DWORD"
 oShell.regWrite "HKCU\Console\ScreenColors", 9, "REG_DWORD"
 oShell.run "cscript.exe /NoLogo """ & wscript.scriptfullname & """ tweaked"
 wscript.sleep 5000
 oShell.regwrite "HKCU\Console\FullScreen", kFullScreen, "REG_DWORD"
 oShell.regWrite "HKCU\Console\ScreenColors", kScreenColors, "REG_DWORD"
 set oShell = nothing
 wscript.quit
end if
dim oIn: set oIn = wscript.stdIn
dim oOut: set oOut = wscript.stdOut
oOut.writeLine "press enter to contintue..."
call oIn.readLine
```

