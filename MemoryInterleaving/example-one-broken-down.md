# example one (broken down)

## Suppose we have a 128 byte memory and we are using 8-way, low-order interleaving. What is the structure of the addresses for this memory?

2^7 = 128

2^3 = 8

to find the low order interleaving we need to take 7 away from 3

7 - 3 = 4

this means that the first 4 bits are used to select the byte in the bank, followed by the last 3 bits to select the bank
