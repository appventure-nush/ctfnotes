# **Chapter 4: Crypto**

## Introduction

Cryptography is the practice of secure communication techniques that allow individuals or groups to communicate privately and securely, even in the presence of third parties. It involves the use of mathematical algorithms and protocols to encrypt and decrypt messages, ensuring that only the intended recipient is able to read the message. Cryptography algorithms are some of the most used algorithms in the modern world. In CTFs, we break these encryption methods.

## XOR

XOR (exclusive OR) is a logical operation that takes two input values and produces an output value based on the following table:
| Input 1 | Input 2 | Output |
|---------|---------|--------|
| 0       | 0       | 0      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 0      |

In other words, the output is 1 if either of the inputs is 1, but not both. If both inputs are 1 or both inputs are 0, the output is 0. It is important to note that XOR is a binary operation, meaning that it only works on binary inputs and outputs. XOR is also a commutative operation, meaning that the order of the inputs does not matter. For example, `A XOR B` is the same as `B XOR A`. XOR is also an associative operation, meaning that the grouping of the inputs does not matter. For example, `(A XOR B) XOR C` is the same as `A XOR (B XOR C)`. Another important property of XOR is that it is its own inverse. This means that `B XOR B` is the same as `0` and thus if `A XOR B` is equal to `C`, then `B XOR C` is equal to `A`. This property is useful for breaking XOR encryption.

## Ciphers

A cipher is a method of encrypting a message to conceal its contents from anyone who is not intended to read it. Ciphers use a set of rules, also known as an algorithm, to transform the plain text into ciphertext. There are many different types of ciphers, ranging from simple substitution ciphers to complex modern ciphers that use advanced mathematical algorithms. An important property of ciphers are that they are reversible - the ciphertext can be decrypted to reveal the original plaintext.

### Caesar Cipher

The Caesar cipher is one of the simplest and most well known ciphers. The Caesar cipher is a type of shift cipher, which means that it replaces each letter in the plaintext with a letter that is a fixed number of positions down the alphabet.For example, if we use a shift of 3, then A will be replaced by D, B will be replaced by E, C will be replaced by F, and so on. The Caesar cipher is easy to break, but it can be useful for introducing the concept of encryption to beginners. To encrypt a message using the Caesar cipher, we first need to choose a shift value. For example, if we choose a shift value of 3, then we will use the following substitution table:

`Plaintext: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`
`Ciphertext: D E F G H I J K L M N O P Q R S T U V W X Y Z A B C`

[This](https://algorithm-visualizer.org/uncategorized/caesar-cipher) is a great visualizer to see how the Caesar cipher works.

### Vigenere Cipher

The Vigenere cipher is a type of polyalphabetic substitution cipher, which means that it uses multiple substitution alphabets. The Vigenere cipher uses a series of Caesar ciphers based on the letters of a keyword. To encrypt a message using the Vigenere cipher, we first need to choose a keyword. A keyword stream is formed by repeating the keyword as many times as necessary to match the length of the plaintext. For example, if we choose the keyword `pico` and plaintext `hello` , then the keyword stream will be `picop`. We then use the following substitution table to encrypt the message:  

![Image of Vigenere Cipher](./Images/VigenereTable.png)

For each letter, we let the plaintext letter be the column, and the key letter be the row. For encrypting the first letter of `hello`, we use `h` as the column and `p` is the row, giving us `w`. Eventually we get the ciphertext `wmnzd`.

## Converting Between Base

There could be certain cases where a string of characters is represented in a different base than the one we are used to. For example, a string of characters could be represented in base 16, which is also known as hexadecimal. In this case, we would need to convert the string of characters to base 10 or binary (base 2). This can be done using [CyberChef](https://gchq.github.io/CyberChef/) where you can make certain recipes to convert between bases and also even more. Here is a [great guide](https://www.csnp.org/post/cyberchef-data-decoding-made-easy) and [video](https://www.youtube.com/watch?v=rT_CjwKN380) to learn how to use CyberChef.

There are also some functions in most languages to convert between bases such as `format(integer, 'b')` in Python to convert an integer to binary.

## Hashing Functions

A hashing function is a one-way function that takes an input (which can be a string or file) and produces a fixed-size output. The input can be of any size, but the output is always the same size. Hashing functions are used in a variety of applications, including password storage, data integrity checks, and indexing data in databases. Hashing functions are also designed to be collision-resistant, which means that it is difficult for two different messages to produce the same hash value, however it is still possible and could be a CTF challenge.

### MD5 Hash

The MD5 algorithm takes an input message and processes it through a series of mathematical operations to produce a 128-bit (16-byte) hash value. The resulting hash value is a unique representation of the input message, and any change to the input message will result in a different hash value. MD5 has several vulnerabilities that make it less secure than other hashing functions. One major vulnerability of the MD5 algorithm is that it is prone to collision attacks. This means that it is possible for an attacker to find two different inputs that produce the same hash value when processed through the MD5 algorithm. Another vulnerability of the MD5 algorithm is that it has a relatively short output size of 128 bits (16 bytes). This makes it more susceptible to preimage attacks, which are attacks that aim to find an input that produces a specific hash value.

### SHA-1 Hash

The MD5 algorithm takes an input message and processes it through a series of mathematical operations to produce a 160-bit (16-byte) hash value. SHA-1 has similar vulnerabilities to MD5, such as being prone to collision attacks and preimage attacks. SHA-1 is no longer considered secure, and it is recommended to use SHA-2 or SHA-3 instead, which have a much longer output.

### Hash Collision

A hash collision occurs when two different inputs produce the same hash value when processed through a hashing function. This is also known as a "collision attack". Hashing functions are designed to be collision-resistant, which means that it is difficult for two different inputs to produce the same hash value. However, because the output of a hashing function is always the same size, no matter how large the input is, it is theoretically possible for a collision to occur. This is a good [hash collision guide](https://www.comparitech.com/blog/information-security/what-is-a-collision-attack/) and this is a good [hash collision demo](https://www.mathstat.dal.ca/~selinger/md5collision/). This is a great [writeup](https://medium.com/@shrutiavinodh/md5-collision-attack-lab-a-cryptographic-security-seedlab-448329a57f9b) on how to find a hash collision, while this is a great [video](https://www.youtube.com/watch?v=mGCVKLLjIns).

## Questions

Go to these sites and try some questions. Do not be discouraged if you cannot solve them, as it is a learning process. If you do not understand something, such as what is cuRL, do not be afraid to google and learn new things. If you are stuck, try to look as the hints, but even after that you are still stuck, search online for writeups for the problem. [This](https://www.hackthebox.com/blog/It-is-Okay-to-Use-Writeups) is a good article on why it is okay to use writeups.

* [PicoGym Binary Exploitation](https://play.picoctf.org/practice?category=2&page=1)
* [CryptoHack](https://cryptohack.org/)
* [OverTheWire Krypton](https://overthewire.org/wargames/krypton/)
* [Cryptopals](https://cryptopals.com/)
* [MysteryTwister](https://mysterytwister.org/home/welcome/)
* [Root Me](https://www.root-me.org/en/Challenges/Cryptanalysis/)
* [W3Challs](https://w3challs.com/challenges/list/crypto)

## Additional Resources

* [Cryptobook](https://cryptohack.gitbook.io/cryptobook/)
* [Ciphey (Free Flags)](https://github.com/Ciphey/Ciphey)
* [John the Ripper (Free Flags)](https://github.com/openwall/john)
* [RSACTFTool](https://github.com/RsaCtfTool/RsaCtfTool)
* [wechall.net](https://www.wechall.net/active_sites)
* [wechall challenges](https://www.wechall.net/challs/)
