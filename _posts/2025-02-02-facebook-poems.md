---
title: Old Facebook poems and JSON decoding
---

I have recently disabled my Facebook account. As a pre-requisite step, I exported all my activity data to keep as
backup. Hidden in the dirt, I found again some gold nuggets I almost forgot about. Namely, a bunch of old poems of
dubious literary quality but certain nostalgia value, which I wrote in my youth and in my older ages around 15 years
ago, and published as Facebook notes for my friends to read.

Incidentally, poem mining triggered an interesting little project. As it happens, Facebook JSON export data is encoded
in a weird way. Strings literals appear to be encoded in a byzantine mix of ASCII and UTF-8.

In detail: ASCII characters and symbols are encoded as they are. 1 byte = 1 character. So you have the traditional `\n`,
`\r` etc. escape malarkey. "Extended" characters are escaped as their UTF-8 encoding, as bytes, in which each encoded
byte is itself encoded as a separate "Unicode" codepoint.

So for a character whose UTF-8 encoding is, say two byte `0xC2 0xa9` (&copy;), the Facebook encoding would be
`\u00c2\u00a9` instead of the expected `\u00a9`.

I was hoping for a one-liner to fix this, but I ended up writing some Rust code to extract the poems from that JSON blob
into plain text. You may get better mileage, but less fun, by playing with encoding in Python.

[Here is the quick-and-dirty source code](https://github.com/itadinanta/facebook-archive-reader), should you encounter a similar problem.

And, as a teaser, one of the poems from 2010 which I forgot I had written. In Italian. Expect more.

```
[2010-04-15 23:55:31 UTC]-[2023-04-24 00:44:19 UTC]
Caricatura (per pochi intimi)


Condivido me stesso,
mi faccio strada tra cuori
e visceri,
e cervelli.
Arranco
tra discorsi
e sinfonie

e dipinti
e storie
di altri, e mie.

Faccio i capricci,
batto i piedi,
indosso
il mio muso triste
per attrarre
attenzioni.

Se non le ottengo,
tiro di fionda
ai lampioni.

Espongo la mia anima in vetrina,
e il vetro è infrangibile.
A prova di sarcasmo,
di gelosia, di critica.
Al limite, lo fila
un'amicizia finta.

Per ripararlo,
fortunatamente,
basta una pinta.

Ma non hai che da entrare,
e chiedere
gentilmente,
con un sorriso,
un po' di interesse sincero,
una briciola di cortesia
e non guasta nevvero
per farmi tuo
un po' di pazzia

e, se sei forte,
-perché peso!-
portarmi via.

--Nico 16/04/2010 (WIP)
```
