
# Memory Maps

A memory map is a diagram of the memory system that shows the address range and the memory modules installed in the system. It's used to illustrate the address range for each memory module and the amount of free space in the system.

## Address Lines

The number of address lines required to address a given amount of memory is given by the formula:

$2^n$ where $n$ is the number of address lines required.

The number of address lines required to address a given amount of memory is calculated by taking the base 2 logarithm of the amount of memory.

For example:

- If we want to address 1 byte of memory, we need 1 address line. This is because $2^1 = 2$, and 2 to the power of 1 equals 2. Thus, we need 1 address line to address 1 byte of memory.
- If we want to address 1 KB of memory (1,024 bytes), we need 10 address lines. This is because $2^{10} = 1,024$, meaning we need 10 address lines to address 1 KB of memory.

Additional calculations:

- $2^{20} = 1 \text{ MB} = 1024 \text{ KB} = 1,048,576 \text{ bytes}$
- If we want 32 MB of memory, which is:
  $32 * \text{MB} = 2^{log_2(32)} * 2^{20} = 2^5 * 2^{20} = 2^{25}$.
  This means that we need 25 address lines to address 32 MB of memory.

## Memory Sizes

- $1 \text{ KB} = 2^{10} = 1024 \text{ bytes}$
- $1 \text{ MB} = 2^{20} = 1024 \text{ KB} = 1,048,576 \text{ bytes}$
- $1 \text{ GB} = 2^{30} = 1024 \text{ MB} = 1,073,741,824 \text{ bytes}$
- $1 \text{ TB} = 2^{40} = 1024 \text{ GB} = 1,099,511,627,776 \text{ bytes}$

## Converting To Hexadecimal

> Division Rule and terms: Dividend / Divisor = Quotient + Remainder / Divisor  
> Dividend / Divisor = Quotient  
> Dividend % Divisor = Remainder  

If you have a number expressed as `2` to the power of `n`, you can convert it to hexadecimal by dividing the power `n` by `4` and using the `remainder` as the exponent of `2` multiplied the `quotient` as the exponent of `0x10`.

$2^{n} = 2^r * \text{0x10}^q$

Why does this work?

### Example 1: What is $2^{10}$ expressed in hexadecimal?

Note: $2^4 = 16_{10} = \text{0x10}$

$2^{10} = 2^2 * 2^4 * 2^4 = 2^2 * (2^4)^{2} = 4 * \text{0x10}^2 = 4 * \text{0x100} = \text{0x400}$

Now using the quick trick:

For $2^{10}$  
$q = 10/4 = 2$  
$r = 10 \bmod 4 = 2$  
$2^r * \text{0x10}^q = 2^2 * \text{0x10}^2 =  4 * \text{0x10}^2 = 4 * \text{0x100}= \text{0x400}$

### Example 2: What is $2^{18}$  expressed in hexadecimal?

$2^{18} = 2^2 * 2^4 * 2^4 * 2^4 = 2^2 * (2^4)^{3} = 4 * \text{0x10}^3 = 4 * \text{0x1000} = \text{0x4000}$

Now using the quick trick:

For $2^{18}$  
$q = 18/4 = 4$  
$r = 18 \mod 4 = 2$  
$2^r * \text{0x10}^q = 2^2 * \text{0x10}^4 =  4 * \text{0x10}^4 = 4 * \text{0x1\ 0000}= \text{0x4\ 0000}$

Example3: What is $2^{25}$ expressed in hexadecimal?

$2^{25} = 2^1 * 2^4 * 2^4 * 2^4 * 2^4 * 2^4 * 2^4 = 2^1 * (2^4)^{6} = 2 * \text{0x10}^6 = 2 * \text{0x100 0000} = \text{0x200 0000}$  

Now using the quick trick:

For $2^{25}$  
$q = 25/4 = 6$  
$r = 25 \mod 4 = 1$  
$2^r * \text{0x10}^q = 2^1 * \text{0x10}^6 =  2 * \text{0x10}^6 = 2 * \text{0x100 0000}= \text{0x200 0000}$

[Example Exercise](./memory-maps-exercises.md "Memory Maps - exercises")

---
Copyright &copy; 2024 Mark Crowe <https://github.com/marcocrowe>. All rights reserved.
