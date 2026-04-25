### 🚩 TryHackme Room: OhSINT (CTF Challenge)

[![Badge](https://img.shields.io/badge/Tryhackme-OhSINT%20Badge-e
)](https://tryhackme.com/Zerium.px/badges/ohsint?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=681356d8ed6fef51149de292)

### 📎 Room Link

[Click here to open the room](https://tryhackme.com/room/ohsint)

### 📜 Room Description

What information can you possibly get with just one image file?

### 🎯 Objective

The objective of this room is to find as much information as possible by only having an image, using OSINT techniques.

### 🛠️ Used Tools

| Tool        | Scope                                               |
|-------------|-----------------------------------------------------|
| `Sherlock`  | Find the target's social networks                   |
| `Wigle.net` | Find the target's Wifi SSID                         |
| `ExifTool`  | Metadata extraction                                 |   


### 👁️ Information gathered

| Info                     | Result                          
|--------------------------|----------------------------------------|
| Username                 | `Owoodflint`                           |
| Password                 | `pennYDr0pper.!`                       |
| City                     | `London`                               |
| Email Address            | `owoodflint@gmail.com`                 |
| Personal Website         | `https://oliverwoodflint.wordpress.com/` |
| Wifi BSSID               | `B4:5D:50:AA:86:41`                    |
| Wifi SSID                | `UnileverWifi`                         |
| Holiday Destination      | `New York`                             |
| GPS Position             | `54 deg 17' 41.27" N, 2 deg 15' 1.33" W` |
| User avatar              | `Cat`                                  |


## 📝 Methodology

1. I checked if the image file had metadata that can reveal sensitive information. To do this, I used ExifTool, a tool that lets us see metadata in files. I ran the following command: 
`exiftool WindowsXP_1551719014755.jpg`

<img width="1919" height="1040" alt="image" src="https://github.com/user-attachments/assets/f39d1c8c-85a8-47d4-ac38-06b6d8dacfed" />

2. We can see that there is an important metadata that lets us know the username of the target: `Copyright: OWoodflint`. After that, I performed a more detailed search using `sherlock`, a tool that lets us find all social networks where the user is registered. To start, I executed on my shell this command: `sherlock Owoodflint`.

<img width="1913" height="920" alt="image" src="https://github.com/user-attachments/assets/0ad6089d-3efb-439a-860e-a3cb49b480ae" />


3. With a simple research, I found his github profile. His readme reveals some information that might expose him more, such as city(London), twitter account, email address(owoodflint@gmail.com) and his website(his website can be useful for our osint research, maybe we can find some comments in the HTML code that can help us know more about the target).
   
<img width="1920" height="942" alt="image" src="https://github.com/user-attachments/assets/a3b96c14-3293-4e88-be03-5342a93b65d7" />

4. I visited his website: https://oliverwoodflint.wordpress.com/. There is nothing much to see here, but I found the user's password by inspecting the website's source code. Password found: `pennYDr0pper.!` .

<img width="1920" height="942" alt="image" src="https://github.com/user-attachments/assets/da0f71dc-ae3b-4fd2-934b-b7e7a21a8791" />



5. I viewed the target's X profile, noticing a post that reveals his Wifi BSSID(which is something you should never post online, because it reveals even more information to the attacker):

<img width="1920" height="949" alt="image" src="https://github.com/user-attachments/assets/c514fc22-4383-4f85-bf9c-86e408329428" />




6. We can now utilise the BSSID to find his Wifi SSID, using a tool called [Wigle](https://wigle.net): Wigle is a community-driven database of wireless networks worldwide.
I've put his BSSID in the search bar to see if it was contained in the Wigle's database. The result shows that his Wifi SSID is `UnileverWifi`, which is located in London, the exact city where he currently lives in.

<img width="1920" height="949" alt="image" src="https://github.com/user-attachments/assets/1e667248-413a-4062-ab03-feb1c6bfc3da" />

## 📕 Final Thoughts

We collected all possible information related to our target. This information could be used by a black hat hacker to carry out illegal activities such as doxxing, social engineering, or phishing attacks.
The user exposed themselves too much, mainly due to metadata contained in the image file, which allowed us to build a profile of our target.

## 🛡️ How can we prevent this?

To protect our privacy from metadata, we must be cautious when posting images online, because they often contain a lot of metadata that can reveal sensitive information. We can completely remove metadata from images by using MAT2 (Metadata Anonymisation Toolkit), a tool pre-installed in privacy-oriented Linux distributions like [Parrot OS](https://parrotsec.org) and [Tails OS](https://tails.net).

## ❓ What I learned

This challenge taught me extremely important OPSEC concept: never expose ourselves too much on the internet, everything we say can be used against us. We must think twice before posting something online, because every piece of sensitive information we accidentally share can be used to build a profile about us.

## 🔍 Find me on

[![TryHackMe](https://img.shields.io/badge/TryHackMe-Zerium.px-212C42?style=for-the-badge&logo=tryhackme&logoColor=red)](https://tryhackme.com/p/Zerium.px)

![Discord](https://img.shields.io/badge/Discord-zerium.px-5865F2?style=for-the-badge&logo=discord&logoColor=white)

[![Telegram](https://img.shields.io/badge/Telegram-@Zerium_py-212C42?style=for-the-badge&logo=telegram&logoColor=blue)](https://t.me/Zerium_py)











