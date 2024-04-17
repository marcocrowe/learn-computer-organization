# Moemory Interleaving Example

## Suppose we have a 128 byte memory and we are using 8-way, low-order interleaving. What is thestructure of the addresses for this memory?

### Step 1: calculate the number of address lines needed

The memory has a capacity of 128 bytes. This means that we need 7 address lines to address 128 bytes of memory.

this is because:

$$
2^7 = 128_{10} 
$$#



### Step 2: calculate the number of bits needed to represent the number of ways


The memory is using 8-way, low-order interleaving. This means that we need 3 bits to represent the number of ways.

T