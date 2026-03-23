### TryHackme Room: Neighbour (CTF Challenge)

### Room Link
[Click here to open the room](https://tryhackme.com/room/neighbour)

### Room Description
Check out our new cloud service, Authentication Anywhere -- log in from anywhere you would like! Users can enter their username and password, for a totally secure login process! You definitely wouldn't be able to find any secrets that other people have in their profile, right?

### Objective
The objective of this challenge is to identify a vulnerability in the login page of the website, that can be used to gain unauthorized access to the admin account.

### Vulnerability found
Insecure Direct Object Reference (IDOR)

### How I Proceeded
1. I opened Firefox and navigated to the provided URL: http://10.114.154.203/ .
2. I pressed CTRL+SHIFT+I to open the browser’s developer tools and inspect the HTML structure, so I can understand the website's structure.
3. I noticed default credentials mentioned in the source code: guest:guest. This is the first mistake made by the website developer: he left sensitive comments in the website.
4. I used these credentials to log in to the guest account.
5. I observed the profile URL: http://10.114.154.203/profile.php?user=guest.
6. I recognized this as a potential IDOR vulnerability.
7. I replaced guest with admin in the URL: doing this, I gained unauthorized access to the admin account, exploiting an URL parameter.

### What I've learned
It is extremely important not to leave sensitive information in website source code or comments, as this can help attackers discover vulnerabilities. Additionally, developers must ensure that URL parameters are properly validated and access-controlled, to prevent IDOR and similar attacks.

### Screenshots

Here are the screenshoots of the challenge, explaining them.

In the first one, I inspected the HTML structure of the website, seeing if there were sensitive information about the website. As we can see, the comments clearly show us that there is something wrong with the admin account:
<img width="1600" height="786" alt="image" src="https://github.com/user-attachments/assets/d5831dcf-80fd-4c64-b8a4-7eac1be5694a" />
In the second one, I gained unauthorized access to the admin account using IDOR.
<img width="1600" height="786" alt="image" src="https://github.com/user-attachments/assets/4ef23f6e-58af-4658-889e-f28ffabb40f8" />












