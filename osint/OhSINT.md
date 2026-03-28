### TryHackme Room: OhSINT (CTF Challenge)

### Room Link

[Click here to open the room](https://tryhackme.com/room/ohsint)

### Room Description

What information can you possibly get with just one image file?

### Objective

The objective of this room is to find as much information as possible by only having an image, using OSINT techniques.

### Used Tools

| Tool        | Scope                            |
|-------------|----------------------------------|
| `Sherlock`  | Find the target's social networks|
| `Wigle.net` | Find the target's Wifi SSID      |
| `ExifTool`  | Metadata extraction              |   


### Information gathered

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

## Methodology

1. I checked if the image file has metadata that can reveal sensitive information. To do this, I used ExifTool, a tool that lets us see metadatas in files. I ran the following command: 
`exiftool WindowsXP_1551719014755.jpg`

<img width="1919" height="1040" alt="image" src="https://github.com/user-attachments/assets/f39d1c8c-85a8-47d4-ac38-06b6d8dacfed" />

2. We can see that there is an important metadata that lets us know the username of the target: `Copyright: OWoodflint`. After that, I did a research on Google to see what I could find.

3. With a simple research, I found his github profile. His readme reveals some information that might expose him more, such as city(London), twitter account, email address(owoodflint@gmail.com) and his website(his website can be useful for our osint research, maybe we can find some comments in the HTML code that can help us know more about the target).
   
<img width="1920" height="942" alt="image" src="https://github.com/user-attachments/assets/a3b96c14-3293-4e88-be03-5342a93b65d7" />

4. I visited his website: https://oliverwoodflint.wordpress.com/. There is nothing much to see here, but I found the user's password by inspecting the website's source code. Password found: `pennYDr0pper.!` .

<img width="1920" height="942" alt="image" src="https://github.com/user-attachments/assets/da0f71dc-ae3b-4fd2-934b-b7e7a21a8791" />



5. I viewed the target's X profile, noticing a post that reveals his Wifi BBSID(which is something you should never post online, because it reveals even more information to the attacker):

<img width="1920" height="949" alt="image" src="https://github.com/user-attachments/assets/c514fc22-4383-4f85-bf9c-86e408329428" />








