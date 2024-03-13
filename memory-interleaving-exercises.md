# Memory-Interleaving

## Introduction

## Examples

### Example 1

For a 32K x 8 memory that uses 16-way, high-order interleaving, find the location (chip and offset) of the following address:001 0000 0010 0111

#### Solution

For `16 way` , `high-order` interleaving, The first $\log2(16) = 4$ bits are used to select the chip. The remaining 11 bits are used to select the offset. The address is divided into two parts: the chip address and the offset address.

| Chip Address | Offset Address |
|--------------|----------------|
| 0010         | 000 0010 0111  |
| Chip 2       | Offset 39      |

### Example 2

For a 32K x 8 memory that uses 8-way, low-order interleaving, find the location (chip and offset) of the following address: 001 0000 0010 0111

#### Solution

For `8-way` , `low-order` interleaving, the last $\log2(8) = 3$ bits are used to select the chip. The first 12 bits are used to select the offset. The address is divided into two parts: the chip address and the offset address.

| Offset Address | Chip Address |
|---------------:|-------------:|
| 0010 0000 0100 |          111 |
|     Offset 516 |       Chip 7 |

---
Copyright &copy; 2024 Mark Crowe <https://github.com/marcocrowe>. All rights reserved.
