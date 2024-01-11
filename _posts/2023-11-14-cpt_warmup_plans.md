---
toc: false
comments: true
layout: post
title: Ideation for CPT warmup
description: Plans and diagrams for the CPT Warmup
courses: {compsci: {week: 13}}
type: plans
---
# Binary Exploration Website Ideation
- Pull together many binary-related applications/features for the user to explore

## Needs
- 5 binary-related features
- SASS theme(Merry Christmas)


## Random Color Generator

- Validate RGB Values
- Convert RGB Decimal to Binary
- Have sample RGB value input (decimal)
- Display color in RGB format
- Displaying converted RGB values in binary

<img src = "https://media.discordapp.net/attachments/1174540464951676969/1174591418451369994/image.png?ex=65682681&is=6555b181&hm=10da97d668d2ce6c0e1dea11fd5e9fd743ab5dacc88778b282c5017d15aa1c79&=&width=1333&height=993">

- Key Commits

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/9da25de7e4f114a33fdb5028e7b4d3d236659a6e">js color generator</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/2d1eac0c2044606f30e2e8d65da9342d9a673608">python binary colorgen</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/a9aa10d3a696960b662604dc98f4ea624c7f5fe5">sample color input</a>

## Binary Sheep Counter

- Allow the user to count but in binary because its cooler
- As the user counts in binary, you convert the current values to RGB and change the color of the sheep
    - Relationship between RGB and the binary values
- Make a moving sheep to make it more interesting
- Maybe a multiplier to make the color changing happen faster
<img src="https://media.discordapp.net/attachments/770342230925246505/1174724123272953926/image.png?ex=6568a218&is=65562d18&hm=78d37e8cc067bf8f6063c43e6e3be8927bcf6d896ac199ad47c0508c6e1e5172&=&width=1440&height=356">

## Steganography Encoder:
- convert string you want to hide into binary
-  Read image, get info in each pixel
- convert each into binary
- Modify the least significant bit/ least significant bits (last 1 or last 2) bits to the corresponding bit in the binary string that we made
- save new binary as a new image, then return that image to the user (this image has the encrypted text inside of it)
- make a decrypter, read the least significant bits of each pixel, then add them all to a binary string, then convert that binary string back into a text message

<img src="https://media.discordapp.net/attachments/1174540464951676969/1174593785125158952/image.png?ex=656828b5&is=6555b3b5&hm=a7011f9a63a9b4446ba284351661dfa585a85b633f4d4548d6ce0ea363583709&=">

## Password combiner:
- 2 passwords → convert both to binary
- Use logic gates to combine the two passwords into one
- Convert back into letters and numbers and display new password
- Logic gates:
    - AND gate
    - OR gates
    - XOR gate
    - NOR gate
    - NAND gate

<img src="https://media.discordapp.net/attachments/1138198617463730330/1174619521932337213/image.png?ex=656840ad&is=6555cbad&hm=fb0a2f5c9057b18b79ed28cdf7d0c6dec4e6523acc454bf9861753e21bee49c6&=">

## Ascii Art Generator:
- Object as input and generates ASCII art from the image.
- Processing each pixel in the image, converting RGB values to binary, and determining whether to use '*' (foreground) or ' ' (background) based on specific criteria defined in the isForeground function
-  Determines whether a pixel should be considered part of the foreground based on a binary value
- Converting each pixel's RGB values to binary used as determination

<img src="https://cdn.discordapp.com/attachments/1174540464951676969/1174883955951026247/Ideation_for_Ascii_Art.png?ex=656936f3&is=6556c1f3&hm=da5e0c773a9140d4eef517b8573d4c673fbe1bec18ce0fb8bd403738afa104c2&">

## Feedback

- 0.98/1.00 for Lakshanya and Hanlun
- Excellent Ideation and Code, space for minor improvements

- 0.97/1.00 for Matthew, Aditya, and Trevor
- Overall great, but could work a little bit more on organization of ideation

## Both teams

- Great theme, liked the Christmas design
- Easy to read
- All the codes work great
- Clearly expressed ideas and plans


<script src="https://utteranc.es/client.js"
        repo="trevorhuang1/cpt_warmup"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>