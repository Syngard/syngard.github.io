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

The second challenge revolves around an Android APK. My fist reflex was to open the app inside [JADX](https://github.com/skylot/jadx). From the `AndroidManifest.xml` file, we can see that the Launcher Activity is `com.example.supersecretappui.login.LoginActivity`. From this activity, a listener is defined for the login button. It calls `LoginActivity.this.loginViewModel.login()` when clicked. 
![](/images/posts/BZHCTF2022/RE1.png)
This function in turn calls `LoginRepository.login()`. A few calls deep, we end up at the bottom of the well, where the submitted password is actually checked, in the `verifiedPassword()` function.



### Rusty Hammer


### Challenge 4

This challenge was published during the night in a new "Android" category but it was still kind of a reversing challenge.

## Others


