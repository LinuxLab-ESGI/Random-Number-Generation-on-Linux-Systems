# Random Number Generation on Linux systems

*This write-up has been written to complete the presentation and to deal in depth with the subject in detail.*
__________
## Technical terminology : 

At first we need to define several concepts and technical terms to completely understand the process of random number generation on Linux systems.

### First of all, what is the entropy ?

*The entropy means a measurable physical property that is particularly  associated with a state of **disorder**, **randomness**, **uncertainty** or even **chaos**.*

So, better the entropy is, more qualitative the random values generation is !

Let's take an example for computer science. Look at this two differents strings :

String 1 : **aDf!F62?g3W8m$**

String 2 : **aaZz$qwQ22Z7zPP**

In this simple example, we can easily guess which string has a better entropy. Here it is the string 1 !

But why ?

We can notice that the string 1 has different characters and no repetition of identical ones. However, we can see in the string 2 that there are several repetitions of '2', 'a', 'z'...

### What are the special files on Linux distributions ?

*A **device file** or **special file** is an interface to a **device driver** that appears in a file system as if it were an ordinary file.*

### Why we talk about *pseudo-random* generation ?

*Pseudo-random number generation creates a sequence of numbers that approximates the properties of perfect random numbers as closely as possible. It's based on **mathematical algorithms**.*

### What is a seed in pseudo-random number generation ?

*The seed is the **entry point** of the pseudo-random generation algorithm. This value is defined explicitly by the user or directly with a default value like the system timestamp for example. The purpose of the seed is to allow the user to **lock** the pseudo-random number generator, to **prevent replicable analysis**.*

## /dev/random VS /dev/urandom

## Other random data source devices

## Appendix - Sources and References

__________
Updated : 09/10/2021, Author : Xen0rInspire
