Many Time Pad
=====

Assignment
-----
Demonstrate why you should never reuse a stream cipher key. Given several ciphertexts that were all encrypted with the same key, extract the key and decode the last ciphertext.

Key Ideas
-----

Assume that the stream cipher XORs the message and the key to get the ciphertext. Then if we XOR two ciphertexts that used the same key, the result is the two original messages XORed together.
- m1 $\oplus$ key = ct1
- m2 $\oplus$ key = ct2
- ct1 $\oplus$ ct2 = m1 $\oplus$ key $\oplus$ m2 $\oplus$ key = m1 $\oplus$ m2

Given the messages are in [ASCII](http://www.asciitable.com/), a space character XORed with a character in the set [a-zA-Z] will result in the same character but in the opposite case.
- Example: 'A' $\oplus$ ' ' = 'a'

Given this, if we XOR two ciphertexts, for every space character in one message we can decode the corresponding character in the other message and vice versa.

Once we have a ciphertext character paired with a message character, we can calculate the corresponding byte of the key
- ct $\oplus$ m = key

If we have enough unique ciphertexts to combine, we can extract the entire key

Algorithm
-----


Alternative Solution
-----
See [this](https://github.com/mithi/simple-cryptography/tree/master/01-many-time-pad#core-idea) alternative solution that uses three ciphertexts to triangluate which message is a space, rather than guessing.
