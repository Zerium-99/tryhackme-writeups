### TryHackme Room: Neighbour (CTF Challenge)

### Room Link
[Click here to open the room](https://tryhackme.com/room/neighbour)

### Room Description
Check out our new cloud service, Authentication Anywhere -- log in from anywhere you would like! Users can enter their username and password, for a totally secure login process! You definitely wouldn't be able to find any secrets that other people have in their profile, right?

### Objective
The objective of this challenge is to identify a vulnerability in the login page of the website, that can be used to gain unauthorized access to the admin account.

### Vulnerability found
Insecure Direct Object Reference (IDOR)

## Methodology

1. I accessed the target web application at the provided IP address.

2. I inspected the website using browser developer tools to understand its structure and identify any potential sensitive information.

3. I discovered default credentials (guest:guest) in the HTML comments, which indicates poor security practices.

4. I used these credentials to log in as a guest user.

5. After logging in, I analyzed the profile URL:
   /profile.php?user=guest

6. I identified this as a potential IDOR vulnerability because the user parameter was directly modifiable.

7. I changed the parameter from guest to admin:
   /profile.php?user=admin

8. This granted unauthorized access to the admin account.

### Screenshots

Here are the screenshots of the challenge, explaining them.

In the first one, I inspected the HTML structure of the website, seeing if there were sensitive information about the website. As we can see, the comments clearly show us that there is something wrong with the admin account:
<img width="1600" height="786" alt="image" src="https://github.com/user-attachments/assets/d5831dcf-80fd-4c64-b8a4-7eac1be5694a" />
In the second one, I gained unauthorized access to the admin account using IDOR.
<img width="1600" height="786" alt="image" src="https://github.com/user-attachments/assets/4ef23f6e-58af-4658-889e-f28ffabb40f8" />

### Source Code Analysis

While inspecting the HTML source code using browser developer tools, we can see a comment with sensitive information.
The comment reveals:
1. Default credentials: `guest:guest`
2. Reference to an existing `admin` account

This represents poor security practice, as sensitive information should never be exposed in client-side code.

```
<html lang="en"><head>
    <meta charset="UTF-8">
    <title>Login</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body{ font: 14px sans-serif; }
        .wrapper{ width: 360px; padding: 20px; margin: 0 auto; }
    </style>
</head>
<body>
    <div class="wrapper">
        <h2>Login</h2>
        <p>Please fill in your credentials to login.</p>

        
        <form action="/index.php" method="post">
            <div class="form-group">
                <label>Username</label>
                <input type="text" name="username" class="form-control " value="">
                <span class="invalid-feedback"></span>
            </div>    
            <div class="form-group">
                <label>Password</label>
                <input type="password" name="password" class="form-control ">
                <span class="invalid-feedback"></span>
            </div>
            <div class="form-group">
                <input type="submit" class="btn btn-primary" value="Login">
            </div>
            <p>Don't have an account? Use the guest account! (<code>Ctrl+U</code>)</p>
            <!-- use guest:guest credentials until registration is fixed. "admin" user account is off limits!!!!! -->
        </form>
    </div>

</body></html>
```

### What I Learned

This challenge demonstrates the risks of exposing sensitive information in source code comments, such as default credentials.

Additionally, it highlights the importance of properly validating and authorizing access to user-controlled parameters. Without proper access control, attackers can exploit vulnerabilities like IDOR to access unauthorized data or accounts.












