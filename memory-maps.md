# Memory Maps

2^20 = 1 MB

$$2^{20} = 1MB = 1024 KB = 1,048,576 bytes$$

If we want 32 MB of memory, that is 32 ($$ 2^5$$) times 1 MB. This means that we need 25 (5 for 32 and 20 for a megaByte) address lines. This is because 32 MB = 2^5 x 2^20 = 2^25. This means that we need 25 address lines to address 32 MB of memory.

$$2^{30} = 1GB = 1024 MB = 1,073,741,824 bytes$$

$$2^{40} = 1TB = 1024 GB = 1,099,511,627,776 bytes$$

$$2^{50} = 1PB = 1024 TB = 1,125,899,906,842,624 bytes$$

## Example 1

Memory Map for a system with 2GB capacity. Assume the system has 3 x 32MB memory modules residing at the bottom of memory.

Step 1: calculate full address range: 2GB = 2 * GB =  2^1 x 2^30 = 2^31. This means that we need 31 address lines.

$$2^{31} = 2,147,483,648_{10} = 0x8000\;0000$$

31 / 4 = 7 with a remainder of 3. This means that we need 7 hex digits to represent the address.This means that the address range is 0x0000 0000 to 0x7FFF FFFF.

Step 2: calculate the address range for the 3 x 32MB memory modules. Each module is 32MB = 32 * MB = 2^5 x 2^20 = 2^25. This means that we need 25 address lines to address 32MB of memory.

$$2^{25} = 33,554,432_{10} = 0x200\;0000$$

25 / 4 = 6 with a remainder of 1. This means that we need 6 hex digits to represent the address. This means that the address range is 0x000 0000 to 0x1FF FFFF.

Because we start addressing at `0x000 0000` the first module will be addressed from `0x000 0000` to `0x01FF FFFF`. The second module will be addressed from `0x200 0000` to `0x3FF FFFF`. The third module will be addressed from `0x400 0000` to `0x5FF FFFF`.

Step 3

Step 3: How much free space?
2 GB = 2048 MB
2048 MB – 96 MB = 1952 MB

The memory map for the system is as follows:

0x0,000,000 to 0x1,FFF,FFF: 32MB module 1
0x2,000,000 to 0x3,FFF,FFF: 32MB module 2
0x4,000,000 to 0x5,FFF,FFF: 32MB module 3
0x6,000,000 to 0x7,FFF,FFF: 1,920MB of unused memory

## Example 2

Memory Map for a system with 4GB capacity. Assume the system has 2 x
256MB memory modules residing at the bottom of memory

Step 1: calculate full address range: 4GB = 2^2 x 2^30 = 2^32. This means that we need 32 address lines.
Range of addresses is 0000 0000 to FFFF FFFF

