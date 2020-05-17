---
layout: post
title: Alexa on RaspberryPi
---
# Build your own Alexa
## All credit goes to:
- https://richardtech.net/2019/03/alexa-on-raspberry-pi/

How to set up Alexa on the Raspberry Pi
2ND MARCH 2019
 
The Amazon Echo is a small and useful device to have around the home, but if you’re not sure if you really need one and have a Raspberry Pi lay around – you can make your own!
Unfortunately, this won’t bring the full functionality of the Alexa service to the Raspberry Pi. You’ll have the main functionality of Alexa minus the music services like Spotify.
I was able to ask Alexa to play the radio using TuneIn radio, but it was quite buggy and wouldn’t start streaming, but it is still fun to play around with Alexa.
What you’ll need
There are a few things that you’ll need to get everything up and running.
•	Raspberry Pi 3, if you have an older model the Raspberry Pi 2 should work but the Raspberry Pi 1 will not.
•	USB Microphone, I used a podcast-style microphone but any USB microphone will work.
•	Speaker with 3.5mm connection, you’ll need a speaker with a 3.5mm connection so you can connect it to your Pi. I used a Sensport Move Mini.
You can do the set-up via a keyboard and mouse, or you can use SSH.
Register on Amazon
Before you can begin setting up the Raspberry Pi, you’ll need to create an Amazon Developer Account. This can be done by going to Amazon Developer Services and follow the procedure and prompts for creating an account.
Now that you’ve either logged into your Amazon Developer Account or signed up, it’s time to configure the Alexa service under the developer account so that you can use Alexa on the Raspberry Pi.
Go back to the Amazon Developer Services homepage and select “Alexa” from the different options displayed, this will take you to the Alexa developer homepage.
 
Hover over “Your Alexa Consoles”, which can be found at the top right of the webpage, and select “Alexa Built-in Devices”. Click on “Products” and then click the “Create Product” button.
This is where credentials for the Raspberry Pi to connect to the Alexa service will be generated.
Product Information
 Entering the product information
On this screen, you’ll need to enter a Product name and Product ID. I chose to enter AlexaPi, but you can choose your own name if you’d prefer.
Select “Device with Alexa built-in” as the product type, and select “Other” as the product category, enter AlexaPi into the category and description text boxes.
There are a few more checkboxes and buttons to click below, so let’s do those too. Check “Hands-free” for “How will users interact with your product?” and then for the remaining buttons, select no for all of them. Click “Next”.
Now you need to create a Security Profile for the product you’ve just created. Click “Create New Profile” and give it a name and description. Again, click “Next”.
Now we’ve completed the initial setup of the product, we need need to add some URLs to the “Allowed Origins” and “Allowed Return URLs” section at the buttom of the page.
For this section, you’ll also need the IP address of your Raspberry Pi. To get this you can type ifconfig into the terminal on your Pi or you can use the Adafruit Pi Finder.
 Typing in the allowed origin and return URLs
Under “Allowed Origins” add http://localhost:5050, https://localhost:5050,http://your.raspberry.pi.ip:5050 and https://your.raspberry.pi.ip:5050.
Then fill in the allowed return URLs with http://localhost:5050/code, https://localhost:5050/code, http://your.raspberry.pi.ip:5050/code and https://your.raspberry.pi.ip:5050/code.
Replace your.raspberry.pi.ip with the IP address of your Raspberry Pi. In my case, my Raspberry Pi’s IP address was 192.168.0.219.
Once you’ve done that, agree to the terms and conditions and click “Finish”.
 
Now some capabilities need to be added to the product, so, click on the product name and click “Capabilities” on the left hand side. Check “Named Timers and Reminders” and “Display Cards” and “Display Cards with Text”.
Once you’ve done that, click the “Update” button at the bottom of the page and it’s time to move over to the Raspberry Pi.
I’d recommend that you grab a USB stick and make a text file containing the Client ID, Client secret and Security Profile ID. If you’re using SSH, you don’t need to worry about copying them to a USB.
The client ID and secret can be found on any page under the product you’ve created and the Security Profile ID can be found on the “Security Profile” tab.
It will be a lot easier to copy and paste these into your Raspbian terminal than type it in manually as it is very long.
Installing AlexaPi
Now with all the preparation out the way, it’s time to install the Alexa service to the Raspberry Pi. To do this, we shall be using a piece of software called AlexaPi.
Although AlexaPi is no longer under active development, it still manages to work well at the time of this tutorial.
 Raspbian terminal
The first step will be to make sure your Raspberry Pi is up and running and open up the terminal.
First of all we need to make sure we are in the /opt directory by typing in
cd /opt
Since AlexaPi is hosted on GitHub, we’ll also now need to make sure that git is installed
sudo apt-get install git
Now we can clone the AlexaPi repository to the storage on the Raspberry Pi
sudo git clone https://github.com/alexa-pi/AlexaPi.git
Now that AlexaPi has been downloaded, it’s time to run the setup script
sudo ./AlexaPi/src/scripts/setup.sh
From here, you’ve got to follow the prompts that show up in the terminal, many of them will be filled in but you will be asked whether you want AirPlay functionality, Alexa to automatically run on startup and also to enter your Amazon product credentials that we created earlier.
 Entering the Device Type ID/Product ID
When asked to enter your Device Type ID, enter the Product ID that you created.
Once you’ve done that you’ll need to copy and paste your Client ID, Client secret and Security Profile ID into the terminal.
Once you’ve entered those, you can browse to the URL displayed in the terminal of the Raspberry Pi and log into your Amazon account.
Now you can press Ctrl+C to close the Window and AlexaPi is set up!
Configuring Raspbian
The final stage is to make sure Raspbian has the correct configuration so that AlexaPi will work without any issues, so we’re going to change the boot mode and audio output settings.
First of all, let’s open up the Raspberry Pi configuration screen
sudo raspi-config
Now, you’ll want to go down to the “Boot Options” option and select “Desktop / CLI” and select “Console” as the boot option.
AlexaPi has some issues when booting into the desktop mode, so changing the boot mode to the console will resolve these.
The next step will be changing the audio output.
Go down to the “Advanced Options” tab and select “Audio”. Here you can override the automatic settings and force the Raspberry Pi to use the 3.5mm output by selecting “Force 3.5mm (‘headphone’) jack”.
Now that you’ve done that, you can go across to “Finish” at the bottom and reboot!
When your Raspberry Pi boots back up, you should hear Alexa say “Hello”. Now you have Alexa running on your Raspberry Pi.

useful YOUTUBE LINK
https://www.youtube.com/watch?v=bWzTdv5HbVU&list=PLcNBi9bxhz4AHoVQqFKSiO9lx07pmsb1U&index=26
