---
layout: post
title: BreizhCTF 2022 Writeups
categories: [CTF, Android]
---

BreizhCTF is an event held in Rennes every year around the months of March-April. This year marked the third time I participated in the event, two years after the last one was held because of the pandemic. T

## Reverse Engineering

There were six reversing challenges in the CTF, of which I managed to solve four. The last challenge wasn't flagged by any team during the event. I'll try to post a writeup if I manage to solve it later.

### Baby

The first challenge was called Baby. It features a 64-bit ELF file. Given the name, it was pretty obvious that there was nothing complicated going on.
```
$ strings baby | grep BZHCTF
BZHCTF{b4by_r3_f0r_y0u_g00d_luck!!}
```

### Private App

The second challenge revolves around an Android APK. My fist reflex was to open the app inside [JADX](https://github.com/skylot/jadx).

### Challenge 3

### Challenge 4

This challenge was published during the night in a new "Android" category but it was still kind of a reversing challenge.

## Others


