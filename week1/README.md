Many Time Pad
=====

Assignment
-----
Demonstrate why you should never reuse a stream cipher key. Given several ciphertexts that were all encrypted with the same key, extract the key and decode the last ciphertext.

Key Ideas
-----

Assume that the stream cipher XORs the message and the key to get the ciphertext. Then if we XOR two ciphertexts that used the same key, the result is the two original messages XORed together.
- m1 &#8853; key = ct1
- m2 &#8853; key = ct2
- ct1 &#8853; ct2 = m1 &#8853; key &#8853; m2 &#8853; key = m1 &#8853; m2

Given the messages are in [ASCII](http://www.asciitable.com/), a space character XORed with a character in the set [a-zA-Z] will result in the same character but in the opposite case.
- Example: 'A' &#8853; ' ' = 'a'

Given this, if we XOR two ciphertexts, for every space character in one message we can decode the corresponding character in the other message and vice versa.

Once we have a ciphertext character paired with a message character, we can calculate the corresponding byte of the key
- ct &#8853; m = key

If we have enough unique ciphertexts to combine, we can extract the entire key

Algorithm
-----
![Alt Text](mtp.png?raw=true)

Alternate Solution
-----
See [this](https://github.com/mithi/simple-cryptography/tree/master/01-many-time-pad#core-idea) alternate solution that uses three ciphertexts to triangluate which message is a space, rather than guessing.
