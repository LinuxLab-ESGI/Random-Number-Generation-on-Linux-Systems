---
marp: true
paginate: true
color: #ffff
backgroundColor: #2A2A2A
header: '![width:100px height:100px](./img/logo.png)'
footer: "**10/11/2021 - Nicolas F**"
author: Xen0rInspire
---
<style>
section {
  font-family: 'Century Gothic', serif !important;
  font-size: 26pt
}
</style>
<!-- _class: invert -->

# Random Number Generation on Linux Systems <!-- fit -->

How does it work ?

---
<!-- _class: invert -->

# Technical Terminology

- Entropy
- Special files on Linux distributions
- Pseudorandom number generation (PRNG)
- Seed (in a random number generator context)

---
<!-- _class: invert -->

# What is the entropy ?

---

<!-- _class: invert -->

*The entropy means a measurable physical property that is particularly  associated with a state of **disorder**, **randomness**, **uncertainty** or even **chaos**.*

---
<!-- _class: invert -->

# Example in computer science
<br>

String 1 : `aiK!l0bUMud5?2`

String 2 : `aaaAbkkKmmB99b`

---
<!-- _class: invert -->

# Example in computer science
<br>

String 1 : `aiK!l0bUMud5?2` &larr; Better entropy

String 2 : `aaaAbkkKmmB99b`

---
<!-- _class: invert -->

# What are the special files on Linux distributions ?

---

<!-- _class: invert -->

*A **device file** or **special file** is an interface to a **device driver** that appears in a file system as if it were an ordinary file.*

---

<!-- _class: invert -->

<br>

## Block devices

```bash
/dev/sda
/dev/nvme
/dev/vda
/dev/cdrom
```

## Characters devices

```bash
/dev/random
/dev/urandom
/dev/zero
/dev/ttyX # where X is a number
```
---

<!-- _class: invert -->

# Why we talk about "*pseudo-random*" generation ?

---

<!-- _class: invert -->

*Pseudo-random number generation creates a sequence of numbers that approximates the properties of perfect random numbers as closely as possible. It's based on **mathematical algorithms**.*

---

<!-- _class: invert -->

# What is a seed in pseudo-random number generation ?

---

<!-- _class: invert -->

*The seed is the **entry point** of the pseudo-random generation algorithm. This value is defined explicitly by the user or directly with a default value like the system timestamp for example. The purpose of the seed is to allow the user to **lock** the pseudo-random number generator, to **prevent replicable analysis**.*

---

<!-- _class: invert -->

# /dev/random vs /dev/urandom

The most common special files to generate random numbers 

---

<!-- _class: invert -->

# /dev/random

- High entropy quality
&rarr; Blocks the reading process if the entropy isn't enough
- Can rely on hardware peripherals

<br>

Used to generate SSH keys, for LUKS encryption...

---

<!-- _class: invert -->

# /dev/urandom

- Lower entropy quality
&rarr; Doesn't block the reading process no matter how much entropy
- Better to use for long processes

<br>

Used to wipe disks (shred command for example)

---

<!-- _class: invert -->

# Other random data source devices

Not implemented on every Linux distributions

- **/dev/arandom** : Generates high-quality pseudo-random output data (based on RC4)

- **/dev/prandom** : Simple pseudo-random generator

- **/dev/srandom** : This device returns reliable random data even if sufficient entropy is not currently available (based on MD5)

---

<!-- _class: invert -->


![bg fit right](./img/bye.gif) 

# Any questions ?