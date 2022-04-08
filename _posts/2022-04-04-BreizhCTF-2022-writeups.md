---
layout: post
title: BreizhCTF 2022 Writeups
categories: [CTF, Android]
---

BreizhCTF is an event held in Rennes every year around the months of March-April. This year marked the third time I participated in the event, two years after the last one was held because of the pandemic. I went with two friends from my team T35H ([zTeeed](https://www.duboc.xyz/) and T0t0r0) as well as two colleagues from my company, since two people from the team weren't able to come (we had the tickets since two years ago).
We ended up finishing in 12th place out of 99 teams, which was pretty good given that most of us hadn't played CTF in quite some time.

![](/images/posts/BZHCTF2022/BZHCTF2022.png)

## Reverse Engineering

There were six reversing challenges in the CTF, of which I managed to solve four. The last challenge wasn't flagged by any team during the event. I'll try to post a writeup if I manage to solve it later.

### Baby

The first challenge was called Baby. It features a 64-bit ELF file. Given the name, it was pretty obvious that there was nothing complicated going on.
```
$ strings baby | grep BZHCTF
BZHCTF{b4by_r3_f0r_y0u_g00d_luck!!}
```

### Private App

The second challenge revolves around an Android APK. The flag for this challenge is of the form `BZHCTF{*}` where the password used by the app should be put insde the braces. My fist reflex was to open the app inside [JADX](https://github.com/skylot/jadx). From the `AndroidManifest.xml` file, we can see that the Launcher Activity is `com.example.supersecretappui.login.LoginActivity`. From this activity, a listener is defined for the login button. It calls `LoginActivity.this.loginViewModel.login()` when clicked. 
![](/images/posts/BZHCTF2022/RE1.png)
This function in turn calls `LoginRepository.login()` which itself calls another method. A few calls deep, we end up at the bottom of the well, where the submitted password is actually checked, in the `verifiedPassword()` function.
![](/images/posts/BZHCTF2022/RE4.png)
From the caller function, we have the info that the flag is only 8 characters long.
![](/images/posts/BZHCTF2022/RE3.png)
We could also see that the login should be `kalucheAdmin:))` if we wanted to validate the password inside the app but since we're doing it on paper it isn't useful.

The password is checked in three rounds, and character by character. We only have to reverse the operation done one character at a time.
```
pwd[0] ^ '!' == '@'       ==> pwd[0] = '!' ^ '@' = 'a'
pwd[1] ^ 'm' + 36 == 123  ==> pwd[1] = (120 - 36) ^ 'm' = '9'
[...]
pwd[7] == pwd[5] ^ pwd[2] ==> pwd[7] = 'M' ^ ':' = 'w'
```
We end up with `BZHCTF{a9:VbMxw}`



### Floppy 1

This challenge was published during the night in a new "Android" category but it was still kind of a reversing challenge. It is based on a game which look like a copy of Flappy Bird. The first challenge was to find 



### Floppy 2

## Others


