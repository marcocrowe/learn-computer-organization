
# Memory Maps

A memory map is a diagram of the memory system that shows the address range and the memory modules installed in the system. It's used to illustrate the address range for each memory module and the amount of free space in the system.

## Address Lines

The number of address lines required to address a given amount of memory is given by the formula:

$2^n$ where $n$ is the number of address lines required.

The number of address lines required to address a given amount of memory is calculated by taking the base 2 logarithm of the amount of memory.

For example:

- If we want to address 1 byte of memory, we need 1 address line. This is because $2^1 = 2$, and 2 to the power of 1 equals 2. Thus, we need 1 address line to address 1 byte of memory.
- If we want to address 1 KB of memory (1024 bytes), we need 10 address lines. This is because $2^{10} = 1024$, meaning we need 10 address lines to address 1 KB of memory.

Additional calculations:

- $2^{20} = 1 \text{ MB} = 1024 \text{ KB} = 1,048,576 \text{ bytes}$
- If we want 32 MB of memory, which is:
  $32 * \text{MB} = 2^log_2(32) * 2^{20} = 2^5 * 2^{20} = 2^{25}$.
  This means that we need 25 address lines to address 32 MB of memory.

## Memory Sizes

- $1 \text{ KB} = 2^{10} = 1024 \text{ bytes}$
- $1 \text{ MB} = 2^{20} = 1024 \text{ KB} = 1,048,576 \text{ bytes}$
- $1 \text{ GB} = 2^{30} = 1024 \text{ MB} = 1,073,741,824 \text{ bytes}$
- $1 \text{ TB} = 2^{40} = 1024 \text{ GB} = 1,099,511,627,776 \text{ bytes}$

## Converting To Hexadecimal

If you have a power of 2, you can convert it to hex by dividing the power by 4. This gives you the number of hex digits required to represent the address.

To convert $2^{31}$ to hex, we need to divide 31 by 4. This gives us 7 with a remainder of 3. Taking the remainder and using it as an exponent of 2 gives us $2^3 = 8$ followed by 7 hex digits (0s) = 0x8000 0000.

This trick works because dividing any number by 4 gives a remainder of [0, 1, 2 or 3]

$2^3 = 8 \\ 2^2=4\\2^1=2\\2^0=1$

A $2^4$ would give a $16_{10}$ = 0x10

[Example Exercise](./memory-maps-exercises.md "Memory Maps - exercises")

![1710166707411](image/memory-maps/memory-bank.png)
