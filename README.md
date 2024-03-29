# mem1_phonegap

**Trying PhoneGap with Wasm with the game mem1**  
***version: 2.0  date: 2019-04-06 author: [bestia.dev](https://bestia.dev) repository: [GitHub](https://github.com/bestia-dev/mem1_phonegap)***  

![status](https://img.shields.io/badge/obsolete-red) 
![status](https://img.shields.io/badge/archived-red) 
![status](https://img.shields.io/badge/tutorial-yellow) 
![Hits](https://bestia.dev/webpage_hit_counter/get_svg_image/741924057.svg)

Hashtags: #rustlang #game #tutorial  
My projects on Github are more like a tutorial than a finished product: [bestia-dev tutorials](https://github.com/bestia-dev/tutorials_rust_wasm).

All written in Rust Wasm/WebAssembly with Dodrio Virtual Dom.  
The source code of the original app is here:  
<https://github.com/bestia-dev/mem1>  
  
PhoneGap is just a distribution of Cordova. It has the exact same "engine". Just the tooling is somehow different.  
On Win10 the development version is served from PhoneGap CLI with `phonegap serve`.  
  
Running the app in Win10 in Chrome browser works fine from the first try.  
  
But running it on my android 6.0.1 (Galaxy Note 4) with PhoneGap Developer app did NOT work at first.  
I discovered the problem : modern browsers don't allow ajax calls to local files for security reasons.  
And pkg/mem1_bg.wasm is a local file from the perspective of the PhoneGap app.  
Therefor I changed the URL of the wasm file to be served over http:// from my GitHub page and now it works fine.  
This is a temporary solution, but good enough to demonstrate how Wasm works with PhoneGap/Cordova.

```javascript
<script>
    //Browsers don't allow Ajax call to local files for security reasons. 
    //I suppose that Cordova works with local files by default.
    //So I use my wasm file on GitHub over the http protocol.
    //Another solution would be to use cordova-plugin-httpd, but I found 
    //it too complicated for this simple example.
    //wasm_bindgen("pkg/mem1_bg.wasm");
    wasm_bindgen("https://bestia-dev.github.io/mem1_website/pkg/mem1_bg.wasm");
  </script>
```
  
## How to install phonegap for development

Requirements : npm must be installed on Win10. It comes with the installation of NodeJS at <https://nodejs.org>.
It installs also the "node.js command prompt". You can find it in Start.  

1\. Win10 : in the "node.js command prompt" run

```bash
npm install -g phonegap@latest
```

2\. Android : install PhoneGap Developer app from Google Play Store

## Cloning the code

3\. Clone this repository. It will create a new folder.

```bash
git clone https://github.com/bestia-dev/mem1_phonegap
```

4\. Move to that folder

```bash
cd mem1_phonegap
```

This code example is based on the Hello sample generated by PhoneGap CLI.  
Inside the www folder I added the folders: www/pkg and www/content  
and the files www/index.html and www/css/mem1.css.  

## Running on Win10 - development server

5\. Start the development server: in "node-js command prompt".  
Run inside the project folder:

```bash
phonegap serve
```

This will also download and prepare all it needs in the /platforms, /plugin and /modules folders.

## Running on Win10 - in the browser

6\. Open the browser with the URL that the `phonegap serve` has printed. It is usually something like 192.168.0.14:3000
It will open the app in the browser.  
![snap01](https://user-images.githubusercontent.com/31509965/55587238-181e8200-5755-11e9-88eb-f8fb62be581e.png)

## Running on Android - PhoneGap Development app

7\. Start the PhoneGap Developer app  
8\. Type in the URL that the `phonegap serve` has printed. It is usually something like 192.168.0.14:3000  
It will open the PhoneGap app.  

## Creating package APK for Android

9\. Open <https://build.phonegap.com/apps> and Sign Up or Sign In.
10\. I choose "open source" and paste my GitHub link <https://github.com/bestia-dev/mem1_phonegap>.  
There is also the possibility for sending the code as one single ZIP file.  
11\. I clicked "Ready to build" or "Rebuild". If the code is changed in GitHub, there is a button "Update Code".
12\. In the right upper corner there is a QR code to download the APK to the android device.  
When Chrome for Android downloads the APK you can then open it.  
It will ask you for install and standard security questions.  
Android must have enabled installing from Unknown Sources. Usually it can be enabled just for this install only.  
13\. On Android find mem1_phonegap in you programs list and run it.  
  
My build APK package can be found here:  
<https://build.phonegap.com/apps/3526520/share>  

## iPhone iOS 99$ per year

To build a PhoneGap app for iOS you need the Certificate from the Apple Developer Membership.  
That costs 99$ per year. No workaround around that.  
Even for just a test or for a development version on one single smartphone.  
I don't want to pay just to try it once if it actually works.  
I will simply suppose that it does.  
PhoneGap is promising that it will work on all smartphones.

## Programming References

<https://phonegap.com/>  
<https://www.formget.com/phonegap-build/>  
<https://cordova.apache.org/>

## Open-source and free as a beer

My open-source projects are free as a beer (MIT license).  
I just love programming.  
But I need also to drink. If you find my projects and tutorials helpful, please buy me a beer by donating to my [PayPal](https://paypal.me/LucianoBestia).  
You know the price of a beer in your local bar ;-)  
So I can drink a free beer for your health :-)  
[Na zdravje!](https://translate.google.com/?hl=en&sl=sl&tl=en&text=Na%20zdravje&op=translate) [Alla salute!](https://dictionary.cambridge.org/dictionary/italian-english/alla-salute) [Prost!](https://dictionary.cambridge.org/dictionary/german-english/prost) [Nazdravlje!](https://matadornetwork.com/nights/how-to-say-cheers-in-50-languages/) 🍻

[//bestia.dev](https://bestia.dev)  
[//github.com/bestia-dev](https://github.com/bestia-dev)  
[//bestiadev.substack.com](https://bestiadev.substack.com)  
[//youtube.com/@bestia-dev-tutorials](https://youtube.com/@bestia-dev-tutorials)  
