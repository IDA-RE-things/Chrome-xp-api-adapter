# "Win7 API to XP" Adapter DLL for Chromium-based browsers

<hr>

"source-available" (only for me while), lighweight, stripped-down, and fine-tuned alternative to progwrp.dll for Supermium/Thorium (and others unbranded Chromium-based browsers, may be, in the future), running on XP.

<hr>
UPD: Initially I have started this project to be open-source alternative.
But now I decided to open sources only if author of original opens his sources. So, sorry guys. No "Windows vs ReactOS" while :)

<br><br>
<b>Preambula:</b>

The author of the original library did not want to provide the source code for this dll (progwrp.dll), in his open-source Chromium-fork repo. Even after I have detected some bugs inside this dll (one was critical Handles leak in his old SRWLocks implementation, causing whole system disfunction; and another - AccessViolations while thread creations -- the hacking trick inside TLS initialization code to work on XP, was wrong. (and as result he fixed them).

Thus, because I still had no source code, And author had no plans to publish it or show,
I questioned, why I helped (as fact) in proprietary and closed software creation, without any benefit from this: having no access to preview or to beta-versions of the whole browser (which I have recommended to do (as irony here),
having no Collaborator status on the repo, or mention, or thanks anywhere. No links in browser repo commits to "issues", no comments in code to "issues". Nothing. Which then transfered to "patches", lossing commit comments at all, and surfaced in another browser project as their work. 

The end point was, when I have read 3rd person (owner of that another project, not owner of DLL) proposition, that the code of DLL "_not allowed to be reverseengineered_", when he placed this in his (3rd person) github pero near other browser code, with provided PDB (which was originally on my request to debug. And Yes, I was constrained to debuig the problems _in "opensource" repo_, by reverse-engineering DLL, provided in this repo only as binary. Even earlier, than he provided the PDB on my request on "issues", I have created my own PDB for this).
The irony was in that this DLL also based on reverse-engineering of Microsoft Binaries.

I'm started my work _in this day just after this "proposition"_.
I desided to create my own variant of such DLL. And improve it as I want. And do with it what I want.


### How it was done:
_<p align=right>be understandable, and has no unnecessary code and bytes :)</p>_

Because I also was under impression of my research "Unadequate/Wrong Memory allocation algorithms/code. Causing process VirtualSize growing and exceeding 2Gb limith, while only ~400Mb allocated for data, and crash" (and no one planed to fix this).
And shit(bloated) coding style in the Chromium code itself. And fact that Chrome.dll now ~200 Mb in size (while only few code really executed).

My goal from the start was to create _simplest and smallest_ possible version of such DLL, But functioning for me, and allowed me to use the browser on XP SP3 x86.
Write understandable source code, which allowed me now to debug it, modify it and improve as I want; also to debug Chrome.dll problems, when some functions called here.

So I taken Microsoft online documentation (sometimes it will be mentioned in the code comments for reference).
Also I taken my existing experience in susch DLLs creation.
I have spent ~2 weeks of my time to initial creation and then debug/understand some bugs (sometime was hard to find the causes: detect which function from the ~160, was recreated/rewritten wrongly, and causes the _visible bug simptoms_ . But I succesfully found such way).

<hr>

The library I have created, named `Chrome-xp-api-adapter.dll`. To use, it can be renamed to progwrp.dll for existing Chrome.exe/dll binary. (of above browsers)

Сompiled DLL (in Releases section) is only ~20 kb vs 136 kb original.

### Current Limitations:
- Originally intended for `XP SP3 x86` (which I use) (but also works now on: Server2003 SP2, XP SP2) (No x64 native versions (and have no plans for this)). Win7 not requeres such DLL at all, because it {original} just redirects API calls under this OS) (and Thorium builds is example of this). **UPD:** now has x86/x64 versions for Win7+ systems for existring Supermium binaries (and they do job above, but with few lines of code).
- It supports only reach set of locales for simplify and minimize size (English, De, Ru). (But works with another languages to translate pagaes and to show user interface). So more complex implementation may be not requered.
The current implementation _requeres to manually change the language from Settings_. (issue #2)
- Also to simplify and minimize size, All not called functions was replaced by stubs (in addition to existing stubs inside original dll, returning error code). So it can crash on internal __debugbreak(), if Some function called, which was not called on my machine. Though on both of my machines it now works w/o such problems. I dont test it with all possible usage scenarios, like all features of DevTools for ex. (though it works) This alternative intended for usual web browsing for first.
- I think you will not see significant differences, _except on real slow/intermediate machines, especially running on HDD drives_. It can't replace other lack of the whole browser optimizations (and not just changing the compiler switches). So dont expect impossible from this replacement DLL.
- In other cases its just my own alternative implementation. But I use only it on my machines with XP.
- This is just my "Proof of concept" that this DLL can be reproduced and enhanced. And people, who really wants sources and has experience for this, can do it in such way.

- the Full (and not stripped-down) versions os such kind of DLL's I'm use over times (~from 2014 yr, when XP suport was gone here or here), -- in other software on my computers, to be compatible with XP.
<hr>
<p align=right>(c) IDA-RE-things, 2024<br>
https://github.com/IDA-RE-things/Chrome-xp-api-adapter
</p>


