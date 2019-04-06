Things are changing fast. This is the situation on 2019-04-04.
# mem1_phonegap
Trying phonegap with Wasm with the game mem1 written in Rust Webassembly with Virtual Dom.  
On Win10 the development version is served from PhoneGap CLI with phonegap serve.  
Running the app in Chrome browser works fine.  
  
But running it on my android 6.0.1 (Galaxy Note 4) with PhoneGap Developer app does NOT work.  
I cannot try this on iPhone, because Apple does not allow the PhoneGap Developer app.  
  
The index.html content is rendered well until it comes to the javascript for Wasm.  
I don't know why.   

The source code of the original app is here:  
https://github.com/LucianoBestia/mem1   

## How to install phonegap for development
Requirements : npm must be installed on Win10. It comes with the installation of nodejs at https://nodejs.org/en/.
It installs also the "node.js command prompt". You can find it in Start.  
1. Win10 : in the "node.js command prompt" run
```
npm install -g phonegap@latest
``` 
2. Android : install PhoneGap Developer app from Google Play Store

## Cloning the code
3. Clone this repository. It will create a new folder. 
```
git clone https://github.com/LucianoBestia/mem1_phonegap
```
4. Move to that folder 
```
cd mem1_phonegap
```
This code example is based on the Hello sample generated by PhoneGap CLI.  
Inside the www folder I added the folders: www/pkg and www/content  
and the files www/index.html and www/css/mem1.css.  
I had to change the background color to better see the problems.  
I added two lines of text in index.html to see where the problem starts.  
```html
<body>
<h1>first line</h1>
<h2>second line</h2>
<script src="pkg/mem1.js"></script>
  <script>
    wasm_bindgen("pkg/mem1_bg.wasm");
  </script>
  <h2>third line</h2>
</body>
```

## Running on Win10 - development server
5. Start the development server: in "node-js command promt". Run inside the project folder:
```
phonegap serve
```
This will also prepare the platforms and plugin and modules folder and download all it needs.

## Running on Win10 - in the browser
6. Open the browser with the URL the command have printed. Something like 192.168.0.14:3000 
It will open the app in the browser. The application works as intended.  
![snap01](https://user-images.githubusercontent.com/31509965/55613230-61ea8500-57b4-11e9-99b7-36125b15c520.JPG)

In the phonegap server there is a warning, but it still works well:
```
[phonegap] [console.warn] `WebAssembly.instantiateStreaming` failed. Assuming this is because your server does 
not serve wasm with `application/wasm` MIME type. Falling back to `WebAssembly.instantiate` which is slower. 
Original error:
[phonegap]  TypeError: Failed to execute 'compile' on 'WebAssembly': Incorrect response MIME type. 
Expected 'application/wasm'.
```

## Running on Android - PhoneGap Development app
7. Start the PhoneGap Developer app  
8. Type in the URL of the command phonegap serve. Cannot use localhost, because, the android and server are on different IP. 
It will open the app, but it will NOT work correctly.  
It will render index.html till the point where is the Wasm script.  
Then it stops.  
![snap01](https://user-images.githubusercontent.com/31509965/55622044-62d9e180-57c9-11e9-86e1-de1be66aec13.png)

In the phonegap server there is this warning:
```
[phonegap] [console.warn] Content Security Policy has been added: <meta http-equiv="Content-Security-Policy" 
content="default-src * gap: ws: https://ssl.gstatic.com;img-src * 'self' data: content:;style-src 'self' 
'unsafe-inline' data: blob:;script-src * 'unsafe-inline' 'unsafe-eval' data: blob:;">
```

## Creating package APK for Android
9. Open https://build.phonegap.com/apps and Sign Up or Sign In.
10. I choose open source and paste my github link https://github.com/LucianoBestia/mem1_phonegap and choose master branch.  
There is also the possibility of sending the code as one ZIP file.  
11. I clicked "Ready to build" or Rebuild. If the code is changed in Github, there is a button Update Code.
12. In the right upper corner there is a QR for downloading the APK. When open the APK file it will try to install it. Android must have enabled installing from Unknown Sources.

The app works the same as with the PhoneGap Development app. It does not start the Wasm code.

2019-04-06
I think the problem is Browsers don't allow file:// URLs with ajax calls (for security reasons).
And wasm is loaded as ajax call. So I have to put a static file server inside Cordova. Let's try.

## Programming References
https://phonegap.com/  
https://www.formget.com/phonegap-build/  





