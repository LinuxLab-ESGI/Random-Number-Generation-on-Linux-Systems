# Random Number Generation on Linux systems

*This write-up has been written to complete the presentation and to deal in depth with the subject in detail.*
__________
## Technical terminology :

At first we need to define several concepts and technical terms to completely understand the process of pseudo-random number generation on Linux systems.

### First of all, what is the entropy ?

*The entropy means a measurable physical property that is particularly  associated with a state of **disorder**, **randomness**, **uncertainty** or even **chaos**.*

So, better the entropy is, more qualitative the random values generation is !

Let's take an example for computer science. Look at this two differents strings :

String 1 : **aDf!F62?g3W8m$**

String 2 : **aaZz$qwQ22Z7zPP**

In this simple example, we can easily guess which string has a better entropy. Here it is the string 1 !

But why ?

We can notice that the string 1 has different characters and no repetition of identical ones. However, we can see in the string 2 that there are several repetitions of '2', 'a', 'z'...

On Linux systems, we use what we call "special files" and especially two in particular that we will discuss in the second part.

### So, what are the special files on Linux distributions ?

*A **device file** or a **special file** is an interface to a **device driver** that appears in a file system as if it were an ordinary file.*

Few examples of special files that you certainly know :

**Block devices**

```bash
/dev/sda
/dev/nvme
/dev/vda # for virtual disks
/dev/cdrom
```

**Characters devices**

```bash
/dev/random
/dev/urandom
/dev/zero
/dev/ttyX # where X is a number
```

### Why we talk about "*pseudo-random*" generation ?

You may have noticed in the first sentences of this article that I talked about pseudo-random generation and not just random generation.

*Pseudo-random number generation creates a sequence of numbers that approximates the properties of perfect random numbers as closely as possible. It's based on **mathematical algorithms**.*

For sure, it is impossible for our current computers to generate perfectly several random values as a human being would be able to do. That's why we need powerful algorithms and measurable physical properties on which to base, to reach the best possible entropy.

It also exists hardware components dedicated to this purpose such as this PCIe expansion card :

![bg fit right](./img/hardware-pcie-card.jpg) 

Or this more recent component, that we call TPM (you certainly heard about it when Windows 11 was released):

![bg fit right 25%](./img/tpm.png)

These components generate random numbers from a measurable physical process as mentioned earlier. It can be the thermal noise for example or any other source of physical entropy. It is finally from this source that we generate a seed !

### But what is a seed in pseudo-random number generation ?

*The seed is the **entry point** of the pseudo-random generation algorithm. This value is defined explicitly by the user or directly with a default value like the system timestamp for example. The purpose of the seed is to allow the user to **lock** the pseudo-random number generator, to **prevent replicable analysis**.*

## /dev/random VS /dev/urandom

As we mentioned before, on Linux systems, we have to use special files to generate random numbers. These two special files are the most common ones and we can found them in most Linux distributions.

### /dev/random

This special file is generally used for cryptographic purposes. In fact, while you are reading this source of random values, the system is controlling if the values generated have enough entropy. If not, the source of reading process can be blocked by the system. That's why it can't be used for long reading processes.

Moreover, this special file can be interfaced with hardware components such as those mentioned above. It depends of course os the Linux distribution (if the necessary drivers are present) and the hardware configuration of your computer.

For example, to generate SSH keys or for LUKS encryption, we generally use **/dev/random** for a better entropy.

### /dev/urandom

The special file **/dev/urandom** is used in quite different cases. In a reading process of this file, there isn't any entropy check, so the random values generated have a lower entropy quality. That's it could be better to used **/dev/urandom** for longs reading processes because the data stream is not bocked by the system.

For example, the *shred* command (known to overwrite a file/disk to hide its contents, and optionally delete it) uses the special file **/dev/urandom**.

## Other random data source devices

Finally, depending of the Linux distribution, you can have other random values sources with other special files. Here are some examples : 

- **/dev/arandom** : Generates high-quality pseudo-random output data (based on RC4 algorithm)

- **/dev/prandom** : Simple pseudo-random generator (no entropy checks)

- **/dev/srandom** : This device returns reliable random data even if sufficient entropy is not currently available (based on MD5 algorithm)

## Appendix - Sources and References

You can find here all my references that I used to write this article and the presentation :

https://www.techno-science.net/glossaire-definition/Generateur-de-nombres-aleatoires-page-2.html

https://developers.tpm.dev/landing?from=https%3A%2F%2Fdevelopers.tpm.dev%2Fposts%2Frandom-number-generator-tpm2-12528972

https://nixdoc.net/man-pages/OpenBSD/man4/arandom.4.html

https://wiki.archlinux.org/title/Random_number_generation

https://wiki.archlinux.org/title/Device_file

https://en.wikipedia.org/wiki/Hardware_random_number_generator

https://en.wikipedia.org/wiki//dev/random

https://linuxhint.com/dev_random_vs_dev_urandom/

https://webinet.cafe-sciences.org/articles/au-fait-cest-quoi-lentropie/

https://en.wikipedia.org/wiki/Pseudorandom_number_generator

https://linuxconfig.org/identifying-file-types-in-linux


__________
<i>Updated : 01/02/2022, Author : Xen0rInspire</i>
