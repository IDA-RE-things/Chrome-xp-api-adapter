# "Win7 API to XP" Adapter DLL for Chromium-based browsers

<hr>

"source-available", lighweight and faster alternative to progwrp.dll for Supermium/Thorium and others unbranded Chromium-based browsers (may be), running on XP.

<hr>
UPD: Initially I have started this project to be open-source alternative.
But now I decided to open sources only if author of original opens his sources. So, sorry guys. No "Windows vs ReactOS" while :)


### How it was done:
_<p align=right>be understandable, and has no unnecessary code and bytes :)</p>_

My goal from the start was to create simplest and smallest possible version of such DLL, But functioning for me, and allowed me to use the browser on XP SP3 x86.
Write understandable source code, which allowed me now to debug it and modify as I want; also to debug Chrome.dll problems, when some functions called here.

So I taken Microsoft online documentation (sometimes it will be mentioned in the code comments for reference).
Also I taken my existing experience in susch DLLs creation.
I have spent ~2 weeks of my time to initial creation and then debug/understand some bugs (sometime was hard to find the causes: detect which function from the ~160, was recreated/rewritten wrongly, and causes the _visible bug simptoms_ . But I succesfully found such way).

<hr>

The library I have created, named `Chrome-xp-api-adapter.dll`. To use, it can be renamed to progwrp.dll for existing Chrome.exe/dll binary. 

Сompiled DLL (in Releases section) is only ~20 kb vs 136 kb original.

### Limitations:
- Intended for `XP SP3 x86` (may work on Server 2003) (but XP SP2 and less not supported here, same as x64).

<hr>
<p align=right>(c) IDA-RE-things, 2024<br>
https://github.com/IDA-RE-things/Chrome-xp-api-adapter
</p>


