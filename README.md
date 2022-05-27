## Android: How to Install ADB, APK's, and JADX-Gui on Parrot OS
Recently I have dived into the journey of learning how to hack, or more precisely pen-testing. Since I focused previously on Android Pentesting when  I explained how to install Genymotion and VirtualBox on Parrot OS, I thought, why don't I write another tutorial on how to install [ADB](https://developer.android.com/studio/command-line/adb) and [JADX-GUI](https://github.com/skylot/jadx) (jadx-gui) on Parrot OS as it is related and quite easy to do. This tutorial assumes you have Android Studio and Parrot OS installed. A good Android Studio installation tutorial can be found [here](https://tutorialforlinux.com/2021/04/05/step-by-step-android-studio-parrot-linux-installation/).

In case you wonder, the version I use of Parrot is the [Security Edition](https://www.parrotsec.org/download/), which comes with most tools installed.🤠

First, let's go over ADB and JADX-GUI. Android Debug Bridge (ADB) is a command-line tool that lets us communicate with a device, but more importantly for this tutorial, install APKs onto our emulated device. JADX-GUI is at its core a code decompiler, so we can take our APK that we downloaded and pop it into the decompiler and voila, we can see all the source code that it contains!

## Installing ADB & APK's
Once you have started up your Parrot OS system, open up a terminal using CTRL + ALT + T and run the following command: **sudo apt-get update**.
![adb](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xiprt2oi6vc5mu3fuh91.png)
  
Then we can install adb with the following command **sudo apt-get install android-tools-adb**.
![ADB Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dws4aamj5melaoft8u52.png)
 
Once it has been installed, we can check if it "worked" by opening Genymotion and running our installed device. Check my [previous tutorial](https://dev.to/christinecdev/how-to-install-genymotion-virtualbox-on-parrot-os-287p) on how to do this. Once your emulated device is up and running, we can go back to our terminal and type in **adb devices**. We can see that we get a list of devices that are attached, one of which is our emulated device. 

![ADB Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7dxvrdwsfrvrqakb5jx0.png)

From there on, we need to install an APK to install onto our device. An APK put simply, is a packaged app that we can download and install for testing purposes. Twelve-year-old me would be so shocked to know that that is how my friend copied their GTA San Andreas game onto my phone!😶

<img src="https://c.tenor.com/pz0JWTgmDKQAAAAd/san-andreas-gta.gif"/>

The APK that we will download in this tutorial is the Diva APK. You can download the APK [here](https://www.payatu.com/wp-content/uploads/2016/01/diva-beta.tar.gz). Once you have downloaded it, head over to your Downloads folder and extract it by right-clicking and saying extract here.

![ADB Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rwu7wxvkctz7es836ig4.png)

Finally, we can download our apk. Head back into your terminal, making sure you are in the directory of your APK and that you have extracted the DIVA file. Type in the following command: **adb install diva-beta.apk**.

![ADB Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1mw0nhasoo2sgev93zji.png) 

Good job! When we head back to our emulated device we can see that our app is now installed onto our device.😄
![APK Working](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lzcs0piva2xddv9wk0s1.png)
![APK Working](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rmsgvhlnvutzxk09ojqk.png)

## Installing JADX-GUI
Now that we have our ADB and APK installed, we can now use this APK in JADX-GUI to decompile the code. ADB allowed us to access the app. JADX-GUI will allow us to access the app's code. 

<u>**To install JADX-GUI, we can simply do the following in the terminal:**</u>
1. sudo apt-get install jadx
2. git clone https://github.com/skylot/jadx.git
3. cd jadx
4. ./gradlew dist

![JDX-GUI Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/p5fxqq5a9zqo3hwf3w1z.png)
![JDX-GUI Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/29j1a4kjrarxemiehfj0.png)
![JDX-GUI Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1xk4k9dagynwohhnnuq1.png)

Then, we can go over to where we downloaded it, go into **jadx > build > jadx > bin**, and double click on **JADX-GUI**. Select the option to run it in the terminal.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oanilsu8bfzb7shm2ow9.png)
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uuvv5slx911cc7ipjfy0.png)
  
It works! Now we can select our Diva APK that we extracted and pop it into the window that just opened. We can see that we can now access most of the source code of the app.

![JDX-GUI Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/a7v00v131sg83jfl13e4.png)
![JDX-GUI Install Parrot](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lhs4e7rajy2aja9i2r8w.png)

## BONUS: JADX-GUI Bash Script
To have to go to the directory where JADX-GUI is every time we want to open/use it is tedious, and time-wasting. Thus we can create a quick bash script to save on our desktop to quickly run it when needed. In Pluma, type in the following: 

```
#!/bin/bash

cd /home/yourname/Downloads/jadx/build/jadx/bin && ./jadx-gui
```

Save this file as whatever, like **run_jdx_gui**. Save it in the directory of your desktop (or wherever you save your bash scripts), and then you can open up a new terminal and cd into the directory where run_jdx_gui is stored. 

![Bash Script](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x854uzzy4l7g1yjdlizy.png)
![Bash Script](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/75aghidtkbs8hgr8uqig.png)
 
Run the following command: **chmod +x run_jdx_gui**. Now when you click on the script it will open up the terminal and run the app!

![Bash Script](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5lvo1tmrjwdcwr7w5fdl.png)
![Bash Script](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fcy35rmyscwbfp6cv0xd.png)

That's it for now, I hope this made sense. Let me know if you need help. See ya next time!❤️
 
