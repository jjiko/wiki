# Cam2ip
* Download from: https://github.com/gen2brain/cam2ip/releases
	* Get the one that says cv2. Or use this direct download link: <a href="https://github.com/gen2brain/cam2ip/releases/download/1.5/cam2ip-1.5-64bit-cv2.zip">release 1.5</a>
* Extract to somewhere like C:\opt\cam2ip-1.3
**If you put it somewhere else you need to change the paths in all scripts**
* Add script to start cam. *You only really need this.. run it and the camera will run. Increment the index if the camera doesn't work*

**You need to configure the index to match your camera**

`\opt\cam2ip-1.3\cmd-start-cam.bat`
```text
start /B C:\opt\cam2ip-1.3\cam2ip.exe -width 1920 -height 1080 -index=0 1>out.log 2>err.log&
```


* (optional) Add scripts to start cam in background.. use start-cam.bat to start the camera and stop-cam.bat to kill the cam2ip task

`\opt\cam2ip-1.3\invisible.vbs`
```vbscript
CreateObject("Wscript.Shell").Run """" & WScript.Arguments(0) & """", 0, False
```

`\opt\cam2ip-1.3\start-cam.bat`
````batchfile
wscript.exe "C:\opt\cam2ip-1.3\invisible.vbs" "C:\opt\cam2ip-1.3\cmd-start-cam.bat"
````

`\opt\cam2ip-1.3\stop-cam.bat`
```batchfile
Taskkill /IM cam2ip.exe /F
```