# "Win7 API to XP" Adapter DLL for Chromium-based browsers

<hr>

"source-available" (only for me), lighweight, stripped-down, and fine-tuned alternative to progwrp.dll for Supermium/Thorium (and others unbranded Chromium-based browsers, may be, in the future), running on XP.

<hr>
UPD: Initially I have started this project to be open-source alternative.
But now I decided to open sources only if author of original opens his sources. So, sorry guys. No "Windows vs ReactOS" while :)


### How it was done:
_<p align=right>be understandable, and has no unnecessary code and bytes :)</p>_

My goal from the start was to create _simplest and smallest_ possible version of such DLL, But functioning for me, and allowed me to use the browser on XP SP3 x86.
Write understandable source code, which allowed me now to debug it, modify it and improve as I want; also to debug Chrome.dll problems, when some functions called here.

So I taken Microsoft online documentation (sometimes it will be mentioned in the code comments for reference).
Also I taken my existing experience in susch DLLs creation.
I have spent ~2 weeks of my time to initial creation and then debug/understand some bugs (sometime was hard to find the causes: detect which function from the ~160, was recreated/rewritten wrongly, and causes the _visible bug simptoms_ . But I succesfully found such way).

<hr>

The library I have created, named `Chrome-xp-api-adapter.dll`. To use, it can be renamed to progwrp.dll for existing Chrome.exe/dll binary. (of above browsers)

Сompiled DLL (in Releases section) is only ~20 kb vs 136 kb original.

### Current Limitations:
- Originally intended for `XP SP3 x86` (which I use) (but also works now on: Server2003 SP2, XP SP2) (No x64 native versions (and have no plans for this). Can run on Win7 x64 using 32bit and XP-only API). Win7 not requeres such DLL at all, because it just redirects API calls under this OS) (and Thorium builds is example of this).
- It supports only reach set of locales for simplify and minimize size (English, De, Ru). (But works with another languages to translate pagaes and to show user interface). So more complex implementation may be not requered.
The current implementation _requeres to manually change the language from Settings_. (issue #2)
- Also to simplify and minimize size, All not called functions was replaced by stubs (in addition to existing stubs inside original dll, returning error code). So it can crash on internal __debugbreak(), if Some function called, which was not called on my machine. Though on both of my machines it now works w/o such problems. I dont test it with all possible usage scenarios, like all features of DevTools for ex. (though it works) This alternative intended for usual web browsing for first.

<hr>
<p align=right>(c) IDA-RE-things, 2024<br>
https://github.com/IDA-RE-things/Chrome-xp-api-adapter
</p>


