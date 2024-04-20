# Memory Interleaving Example

## Suppose we have a 128 byte memory and we are using 8-way, low-order interleaving. What is the structure of the addresses for this memory?

Step 1: calculate the number of address lines needed

The memory has a capacity of 128 bytes. This means that we need 7 address lines to address 128 bytes of memory.

this is because:

$$
2^7 = 128_{10}
8-way \space low \space order, to \space get \space the \space bits \space log_2(8) = 3 \space
so \space 3 \space bits, last \space 3 \space on \space the \space right, are \space used \space to \space select \space the \space bank.
$$

total of 7, minus 3 for mempry bank address leave 4bits

The first 4 bits are used to select the byte in the bank, followed by the last 3 bits to select the bank

e.g. first address in bank 0 is 0000 in the bank 000

| Offset | Bank   |
| ------ | ------ |
| 4 bits | 3 bits |
| 0000   | 000    |
