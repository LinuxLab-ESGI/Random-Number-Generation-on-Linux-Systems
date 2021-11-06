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
