---
title: 'How I Learned to Stop Worrying about AES and Love the Chacha'
date: 2022-07-17
status: publish
permalink: /how-i-learned-to-stop-worrying-about-aes-and-love-the-chacha
author: TECHNOR471
description: 'AES is not just a defacto standard, it is an actual standard '
type: post
id: 1116
thumbnail: /uploads/2023/02/aes-encryption.webp
category:
    - Tech
tags:
    - aes
    - chacha
    - encryption
    - exploit
---

Way back in the 1800’s, the Irish thought that they had solved the problem of feeding an ever growing population. They started planting Lumper potatoes; since potatoes are propagated vegetatively, all of the subsequent lumper ‘taters were genetic clones – identical to one another.

This seemed like a good idea, a starving population is surely a bigger concern than mono-culture agriculture… I’m sure you know what happened next – the Lumper potatoes were susceptible to rot caused by Phytophthora infestans. These infestans started turning all of the Lumper potatoes into slime, and [one in every eight people in Ireland died in the Great Potato Famine](https://en.wikipedia.org/wiki/Irish_Lumper#:~:text=The%20Irish%20Lumper%20is%20a,an%20estimated%201%20million%20died).

## AES = Lumper Potatoes

I’m sure by now you are wondering what the Great Irish Potato Famine has to do with encryption protocols. Fast forward through history to today and you could make the argument that the encryption space is a mono-culture. AES is everywhere.

![AES](/uploads/2023/02/aes-encryption.webp)

As far as I know there is nothing wrong with [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) in and of itself. It is very effective and efficient. It is fast, highly secure, and widely supported. So widely supported in fact that there are instructions built into CPU’s just for AES in the form of native processor support. AES is also implemented widely on the software side in operating system components and file systems.

### Encryption Standards

AES is not just a defacto standard, it is an actual standard as outlined by the [National Institute of Standards and Technology](https://www.nist.gov/publications/advanced-encryption-standard-aes). NIST established AES as an encryption standard nearly 20 years ago. The https protocol that securely loads this website uses AES. So does your wifi ( if you use WAP2 ), your VPN, and countless other examples.

![Encryption makes modern computing possible ](/uploads/2023/02/encryption.webp)
AES is a block cipher that supports 3 key lengths – 128, 192, and 256-bit encryption. If you use a 256 bit key AES provides excellent long-term security against brute-force attacks. The problem with AES, imho, is that AES is secure until it’s not. And when ( not if ) it’s not you have the same issue as Ireland did back in the 17th century. ALL of the encryption we use and rely on every day for critical tasks begins to rot until it is completely useless.

#### ChaCha – not just a cuban dance

[ChaCha](https://en.wikipedia.org/wiki/Salsa20#ChaCha_variant) is a variant of Salsa20; they are both stream ciphers developed by Daniel J. Bernstein. ChaCha is based on a pseudorandom function using add-rotate-XOR (ARX) operations — 32-bit addition, bitwise addition (XOR) and rotation operations. This is a good video to see [this process visualized](https://youtu.be/UeIpq-C-GSA?t=163).

Obviously the main consideration of encryption is securing data. Again, to the best of my knowledge, ChaCha is as secure as AES is. The second consideration for encryption is that it works quickly. This is important not only so people will actually use it but also as it relates to security. If an algorithm takes too long to write to a hash table for example, it gives potential attackers a vector to exploit.

Interestingly on a level playing field ( meaning that there is no hardware acceleration or instruction written for it in the OS ) ChaCha is FASTER than AES. In practice this means it is ideal for small embedded computers, IOT, smart cards etc.

##### It also means that it is a worthy alternative to AES writ large.

As I like to try and practice what I preach I am using an npm based implementation of ChaCha for authentication in the app I have been building for the last couple of months. It is a little more difficult and has taken a little longer than it would have going with the de facto standard, but it has been rewarding getting to know encryption at a more basic level. I have studied cryptography quite a bit, but implementing an auth system from scratch without using the default tooling has been quite educational.

And it’s not often that you can make an analogy between 17th century agriculture and 21st century encryption. So I got that goin’ for me, which is nice..