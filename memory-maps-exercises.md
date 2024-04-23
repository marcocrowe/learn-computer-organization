# Memory Maps exercises

A collection of exercises and solutions to help you practice creating memory maps.

## Example 1

Create a Memory Map for a system with 2GB capacity. Assume the system has 3 x 32MB memory modules residing at the bottom of memory.

### Calculate full address range

$2 \text{ GB} = 2 * \text{GB} =  2*2^{30} = 2^{log_2(2)}*2^{30} = 2^1*2^{30} = 2^{31}.$ This means that we need 31 address lines.

$2^{31} = 2, 147, 483, 648_{10} = \text{0x8000 0000}$

### Calculate the address range for the 3 x 32MB memory modules

Each module is 32MB = 32 * MB = $2^{log_2(32)} * 2^{20} = 2^5 * 2^{20} = 2^{25}$. This means that we need 25 address lines to address 32MB of memory.

### Module 1

$2^{25} = 33, 554, 432_{10} = \text{0x0200 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x0200 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x01FF FFFF` |                                        |

### Module 2

`0x0000 0000` - `0x01FF FFFF` is taken, so add `0x01FF FFFF` to the address range

|   | start         | end           |                               |
|---|---------------|---------------|-------------------------------|
|   | `0x0000 0001` | `0x0200 0000` |                               |
| + | `0x01FF FFFF` | `0x01FF FFFF` | (last address of `Module 1` ) |
|   | `0x0200 0000` | `0x03FF FFFF` |                               |

### Module 3

`0x0000 0000` - `0x03FF FFFF` is taken, so add `0x03FF FFFF` to the address range

|   | start         | end           |                               |
|---|---------------|---------------|-------------------------------|
|   | `0x0000 0001` | `0x0200 0000` |                               |
| + | `0x03FF FFFF` | `0x03FF FFFF` | (last address of `Module 2` ) |
|   | `0x0400 0000` | `0x05FF FFFF` |                               |

### Calculate free space

$\text{GB} = 1024\text{ MB} \therefore 2\text{GB} = 2048\text{ MB} $
$2048\text{ MB} -96\text{ MB} = 1952\text{ MB}$
$1, 952\text{ MB} = 1, 952 * 2^{20} = 2, 046, 820, 352_{10} = \text{0x7A00 0000}$

### Answer

|              |     Size | Start Address | End Address   |
|--------------|---------:|---------------|---------------|
| `Free Space` | 1, 952 MB | `0x6000 0000` | `0x05FF FFFF` |
| `Module 3` |    32 MB | `0x0400 0000` | `0x05FF FFFF` |
| `Module 2` |    32 MB | `0x0200 0000` | `0x03FF FFFF` |
| `Module 1` |    32 MB | `0x0000 0000` | `0x01FF FFFF` |

<table>
  <tr><td bgcolor="#e2efd9">0x7FFF FFFF<br/>&nbsp; <br/>&nbsp; <br/>Free Space<br/>&nbsp; <br/>&nbsp; <br/>0x6000 0000</td></tr>
  <tr><td bgcolor="#a5a5a5">0x05FF FFFF<br/>Module 3<br/>0x0400 0000</td></tr>
  <tr><td bgcolor="#4672c4">0x03FF FFFF<br/>Module 2<br/>0x0200 0000</td></tr>
  <tr><td bgcolor="#fbe5d5">0x01FF FFFF<br/>Module 1<br/>0x0000 0000</td></tr>
</table>

## Example 2

Memory Map for a system with 4GB capacity. Assume the system has 2 x
256MB memory modules residing at the bottom of memory

### Calculate full address range

$4\text{ GB} = 4 * \text{GB} =  4*2^{30} = 2^{log_2(4)}*2^{30} = 2^2*2^{30} = 2^{(2+30)} = 2^{32}.$
This means that we need 32 address lines.

$2^{32} = 4, 294, 967, 296_{10} = \text{0x0001 0000 0000}$

|   |              start |                end |                                        |
|---|-------------------:|-------------------:|----------------------------------------|
|   | `0x0000 0000 0000` | `0x0001 0000 0000` |                                        |
| - | `0x0000 0000 0001` | `0x0000 0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0xFFFF FFFF` |                                        |

Address range is `0x0000 0000` to `0xFFFF FFFF` .

### Calculate the address range for the 2 x 256MB memory modules

Each module is 256MB. $256 * 1\text{ MB} = 2^{log_2(256)} * 2^{20} = 2^8 * 2^{20} = 2^{28}$. This means that we need 28 address lines to address 256MB of memory.

### Module 1

$2^{28} = 268, 435, 456_{10} = \text{0x1000 0000}$
$2^{28} = 268, 435, 456_{10} = \text{0x1000 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x1000 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x0FFF FFFF` |                                        |

### Module 2

`0x0000 0000` - `0x0FFF FFFF` is taken, so add `0x0FFF FFFF` to the address range

|   | start         | end           |                               |
|---|---------------|---------------|-------------------------------|
|   | `0x0000 0001` | `0x1000 0000` |                               |
| + | `0x0FFF FFFF` | `0x0FFF FFFF` | (last address of `Module 1` ) |
|   | `0x1000 0000` | `0x1FFF FFFF` |                               |

### Calculate free space

$\text{GB} = 1024\text{ MB} \therefore 4\text{GB} = 4096\text{ MB} $
$4096\text{ MB} -512\text{ MB} = 3584\text{ MB}$
$3, 584\text{ MB} = 3, 584 * 2^{20} = 3, 758, 096, 384_{10} = \text{0xE000 0000}$

### Answer

|              |     Size | Start Address | End Address   |
|--------------|---------:|---------------|---------------|
| `Free Space` | 3, 584 MB | `0x2000 0000` | `0xFFFF FFFF` |
| `Module 2` |   256 MB | `0x1000 0000` | `0x1FFF FFFF` |
| `Module 1` |   256 MB | `0x0000 0000` | `0x0FFF FFFF` |

## Example 3

Memory Map for a system with 8GB capacity. Assume the system has 3 x 160MB memory modules residing at the bottom of memory, calculate the address range for each module and the amount of free space.

### Calculate full address range

$8\text{ GB} = 8 * \text{GB} =  8*2^{30} = 2^{log_2(8)}*2^{30} = 2^3*2^{30} = 2^{(3+30)} = 2^{33}.$
This means that we need 33 address lines.

$2^{33} = 8, 589, 934, 592_{10} = \text{0x0002 0000 0000}$

|   |              start |                end |                                        |
|---|-------------------:|-------------------:|----------------------------------------|
|   | `0x0000 0000 0000` | `0x0002 0000 0000` |                                        |
| - | `0x0000 0000 0001` | `0x0000 0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000 0000` | `0x0001 FFFF FFFF` |                                        |

Address range is `0x0000 0000 0000` to `0x0001 FFFF FFFF` .

### Calculate the address range for the 3 x 160MB memory modules

Each module is 160MB. $160 * 1\text{ MB} = 160 * 2^{20} = 167, 772, 160_{10} = \text{0x0A00 0000}$

### Module 1

$160\text{MB} =\text{0x0A00 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x0A00 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x09FF FFFF` |                                        |

### Module 2

`0x0000 0000` - `0x09FF FFFF` is taken, so add `0x09FF FFFF` to the address range

|   | start         | end           |                               |
|---|---------------|---------------|-------------------------------|
|   | `0x0000 0001` | `0x0A00 0000` |                               |
| + | `0x09FF FFFF` | `0x09FF FFFF` | (last address of `Module 1` ) |
|   | `0x0A00 0000` | `0x13FF FFFF` |                               |

### Module 3

`0x0000 0000` - `0x13FF FFFF` is taken, so add `0x13FF FFFF` to the address range

|   | start         | end           |                               |
|---|---------------|---------------|-------------------------------|
|   | `0x0000 0001` | `0x0A00 0000` |                               |
| + | `0x13FF FFFF` | `0x13FF FFFF` | (last address of `Module 2` ) |
|   | `0x1400 0000` | `0x1DFF FFFF` |                               |

### Calculate free space

$\text{GB} = 1, 024\text{ MB} \therefore 8\text{GB} = 8, 192\text{ MB} $
$8, 192\text{ MB} -480\text{ MB} = 7, 712\text{ MB}$
$7, 712\text{ MB} = 7, 712 * 2^{20} = 8, 086, 618, 112_{10} = \text{0x0001 E200 0000}$

### Answer

|              |     Size | Start Address      | End Address        |
|--------------|---------:|--------------------|--------------------|
| `Free Space` | 7, 712 MB | `0X0000 1E00 0000` | `0x0001 FFFF FFFF` |
| `Module 3` |   160 MB | `0x0000 1400 0000` | `0x0000 1DFF FFFF` |
| `Module 2` |   160 MB | `0x0000 0A00 0000` | `0x0000 13FF FFFF` |
| `Module 1` |   160 MB | `0x0000 0000 0000` | `0x0000 09FF FFFF` |

<table>
  <tr><td bgcolor="#e2efd9">0x0001 FFFF FFFF<br/>&nbsp; <br/>&nbsp; <br/>Free Space<br/>&nbsp; <br/>&nbsp; <br/>0X0000 1E00 0000</td></tr>
  <tr><td bgcolor="#a5a5a5">0x0000 1DFF FFFF<br/>Module 3<br/>0x0000 1400 0000</td></tr>
  <tr><td bgcolor="#4672c4">0x0000 13FF FFFF<br/>Module 2<br/>0x0000 0A00 0000</td></tr>
  <tr><td bgcolor="#fbe5d5">0x0000 09FF FFFF<br/>Module 1<br/>0x0000 0000 0000</td></tr>
</table>

## Exercise 1

A  video  game  console  has  a  memory  capacity  of  512  MB.  The memory is divided into 4 banks of equal size. Each bank consists of 2 chips, with  each  chip  having  a  capacity  of  64  MB.  Draw  a  memory map that shows the location and size of each memory bank and chip.

1. Find full range of addresses
2. Find range of each chip.
3. Build your map.

Draw a memory map that shows the location and size of each memory bank.

| Bank #   | Chip #   | Size  | Start Address | End Address |
|----------|----------|-------|---------------|-------------|
|          | `Chip 1` | 64 MB |               |             |
| `Bank 3` | `Chip 0` | 64 MB |               |             |
|          | `Chip 1` | 64 MB |               |             |
| `Bank 2` | `Chip 0` | 64 MB |               |             |
|          | `Chip 1` | 64 MB |               |             |
| `Bank 1` | `Chip 0` | 64 MB |               |             |
|          | `Chip 1` | 64 MB |               |             |
| `Bank 0` | `Chip 0` | 64 MB |               |             |

### Calculate full address range

$512\text{ MB} = 512 * 1\text{ MB} =  512*2^{20} = 2^{log_2(512)}*2^{20} = 2^9*2^{20} = 2^{29} = 536, 870, 912_{10} = \text{0x2000 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x2000 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x1FFF FFFF` |                                        |

### Calculate `Bank 0 - Chip 0` address range

$64\text{ MB} = 64 * 1\text{ MB} =  2^6*2^{20} = 2^{(6+20)} = 2^{26} = 67, 108, 864_{10} = \text{0x0400 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x03FF FFFF` |                                        |

Address `Bank 0 - Chip 0` = `0x0000 0000` - `0x03FF FFFF`

### Calculate `Bank 0 - Chip 1` address range

`0x0000 0000` - `0x03FF FFFF` is taken, so add `0x03FF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x03FF FFFF` | `0x03FF FFFF` | (last address of `Bank 0 - Chip 0` ) |
|   | `0x0400 0000` | `0x07FF FFFF` |                                      |

Address `Bank 0 - Chip 1` = `0x0400 0000` - `0x07FF FFFF`

### Calculate `Bank 1 - Chip 0` address range

`0x0000 0000` - `0x07FF FFFF` is taken, so add `0x07FF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x07FF FFFF` | `0x07FF FFFF` | (last address of `Bank 0 - Chip 1` ) |
|   | `0x0800 0000` | `0x0BFF FFFF` |                                      |

Address `Bank 1 - Chip 0` = `0x0800 0000` - `0x0BFF FFFF`

### Calculate `Bank 1 - Chip 1` address range

`0x0000 0000` - `0x0BFF FFFF` is taken, so add `0x0BFF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x0BFF FFFF` | `0x0BFF FFFF` | (last address of `Bank 1 - Chip 0` ) |
|   | `0x0C00 0000` | `0x0FFF FFFF` |                                      |

Address `Bank 1 - Chip 1` = `0x0C00 0000` - `0x0FFF FFFF`

### Calculate `Bank 2 - Chip 0` address range

`0x0000 0000` - `0x0FFF FFFF` is taken, so add `0x0FFF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x0FFF FFFF` | `0x0FFF FFFF` | (last address of `Bank 1 - Chip 1` ) |
|   | `0x1000 0000` | `0x13FF FFFF` |                                      |

Address `Bank 2 - Chip 0` = `0x1000 0000` - `0x13FF FFFF`

### Calculate `Bank 2 - Chip 1` address range

`0x0000 0000` - `0x13FF FFFF` is taken, so add `0x13FF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x13FF FFFF` | `0x13FF FFFF` | (last address of `Bank 2 - Chip 0` ) |
|   | `0x1400 0000` | `0x17FF FFFF` |                                      |

Address `Bank 2 - Chip 1` = `0x1400 0000` - `0x17FF FFFF`

### Calculate `Bank 3 - Chip 0` address range

`0x0000 0000` - `0x17FF FFFF` is taken, so add `0x17FF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x17FF FFFF` | `0x17FF FFFF` | (last address of `Bank 2 - Chip 1` ) |
|   | `0x1800 0000` | `0x1BFF FFFF` |                                      |

Address `Bank 3 - Chip 0` = `0x1800 0000` - `0x1BFF FFFF`

### Calculate `Bank 3 - Chip 1` address range

`0x0000 0000` - `0x1BFF FFFF` is taken, so add `0x1BFF FFFF` to the address range

|   | start         | end           |                                      |
|---|---------------|---------------|--------------------------------------|
|   | `0x0000 0001` | `0x0400 0000` |                                      |
| + | `0x1BFF FFFF` | `0x1BFF FFFF` | (last address of `Bank 3 - Chip 0` ) |
|   | `0x1C00 0000` | `0x1FFF FFFF` |                                      |

Address `Bank 3 - Chip 1` = `0x1C00 0000` - `0x1FFF FFFF`

### Answer

|          |          |  Size | Start Address | End Address   |
|----------|----------|------:|---------------|---------------|
| `Bank 3` | `Chip 1` | 64 MB | `0x1C00 0000` | `0x1FFF FFFF` |
|          | `Chip 0` | 64 MB | `0x1800 0000` | `0x1BFF FFFF` |
| `Bank 2` | `Chip 1` | 64 MB | `0x1400 0000` | `0x17FF FFFF` |
|          | `Chip 0` | 64 MB | `0x1000 0000` | `0x13FF FFFF` |
| `Bank 1` | `Chip 1` | 64 MB | `0x0C00 0000` | `0x0FFF FFFF` |
|          | `Chip 0` | 64 MB | `0x0800 0000` | `0x0BFF FFFF` |
| `Bank 0` | `Chip 1` | 64 MB | `0x0400 0000` | `0x07FF FFFF` |
|          | `Chip 0` | 64 MB | `0x0000 0000` | `0x03FF FFFF` |

<table>
  <tr><td bgcolor="#e2efd9">0x1FFF FFFF<br/>&nbsp; <br/>&nbsp; <br/>Bank 3 - Chip 1<br/>&nbsp; <br/>&nbsp; <br/>0x1C00 0000</td></tr>
  <tr><td bgcolor="#a5a5a5">0x17FF FFFF<br/>Bank 3 - Chip 0<br/>0x1800 0000</td></tr>
  <tr><td bgcolor="#4672c4">0x13FF FFFF<br/>Bank 2 - Chip 1<br/>0x1400 0000</td></tr>
  <tr><td bgcolor="#fbe5d5">0x0FFF FFFF<br/>Bank 2 - Chip 0<br/>0x1000 0000</td></tr>
  <tr><td bgcolor="#e2efd9">0x0BFF FFFF<br/>&nbsp; <br/>&nbsp; <br/>Bank 1 - Chip 1<br/>&nbsp; <br/>&nbsp; <br/>0x0C00 0000</td></tr>
  <tr><td bgcolor="#a5a5a5">0x07FF FFFF<br/>Bank 1 - Chip 0<br/>0x0800 0000</td></tr>
  <tr><td bgcolor="#4672c4">0x03FF FFFF<br/>Bank 0 - Chip 1<br/>0x0400 0000</td></tr>
  <tr><td bgcolor="#fbe5d5">0x0000 0000<br/>Bank 0 - Chip 0<br/>0x0000 0000</td></tr>
  </table>

## Exercise 3

A computer system has a memory with a capacity of 2 GB. The memory is divided into 4 banks, each with a different size.

* Bank 0 has a size of 512 MB
* Bank 1 has a size of 768 MB
* Bank 2 has a size of 256 MB
* Bank 3 has a size of 512 MB

Draw a memory map that shows the location and size of each memory bank.

| Bank #   | Size   | Start Address | End Address |
|----------|--------|---------------|-------------|
| `Bank 3` | 512 MB |               |             |
| `Bank 2` | 256 MB |               |             |
| `Bank 1` | 768 MB |               |             |
| `Bank 0` | 512 MB |               |             |

<table>
  <tr><td bgcolor="#e2efd9">0x____ ____<br/>Bank 3<br/>0x____ ____</td></tr>
  <tr><td bgcolor="#a5a5a5">0x____ ____<br/>Bank 2<br/>0x____ ____</td></tr>
  <tr><td bgcolor="#4672c4">0x____ ____<br/>Bank 1<br/>0x____ ____</td></tr>
  <tr><td bgcolor="#fbe5d5">0x____ ____<br/>Bank 0<br/>0x____ ____</td></tr>
</table>

### Calculate full address range

$2\text{ GB} = 2 * 1\text{ GB} =  2^{1}*2^{30} = 2^{(1+30)} = \\ 2^{31} = 2, 147, 483, 648_{10} = \text{0x8000 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x8000 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x7FFF FFFF` |                                        |

Address range is `0x0000 0000` to `0x7FFF FFFF` .

### Calculate `Bank 0` address range

$512\text{ MB} = 512 * \text{MB} =  512*2^{20} = 2^{log_2(512)}*2^{20} = 2^9*2^{20} = \\ 2^{29} = 536, 870, 912_{10} = \text{0x2000 0000}$

|   | start         | end           |                                        |
|---|---------------|---------------|----------------------------------------|
|   | `0x0000 0001` | `0x2000 0000` |                                        |
| - | `0x0000 0001` | `0x0000 0001` | (Offset by 1 because index is 0 based) |
|   | `0x0000 0000` | `0x1FFF FFFF` |                                        |

Address `Bank 0` = `0x0000 0000` - `0x1FFF FFFF`

### Calculate `Bank 1` address range

$768\text{ MB} = 768 * 1\text{ MB} =  768*2^{20} = 768 * 1, 048, 576 = \\ 805, 306, 368_{10} = \text{0x3000 0000}$

$2^{29} = 805, 306, 368_{10} = \text{0x3000 0000}$

`0x0000 0000` - `0x1FFF FFFF` is taken, so add `0x1FFF FFFF` to the address range

|   | start         | end           |                             |
|---|---------------|---------------|-----------------------------|
|   | `0x0000 0001` | `0x3000 0000` |                             |
| + | `0x1FFF FFFF` | `0x1FFF FFFF` | (last address of `Bank 0` ) |
|   | `0x2000 0000` | `0x4FFF FFFF` |                             |

Address `Bank 1` = 0x2000 0000 - 0x4FFF FFFF

### Calculate `Bank 2` address range

$256\text{ MB} = 256 * 1\text{ MB} = 2^{log_2(256)} * 2^{20} = 2^8*2^{20} = 2^{(8+20)} = \\ 2^{28} = 268, 435, 456_{10} = \text{0x1000 0000}$

`0x0000 0000` - `0x4FFF FFFF` is taken, so add `0x4FFF FFFF` to the address range

|   | start         | end           |                             |
|---|---------------|---------------|-----------------------------|
|   | `0x0000 0001` | `0x1000 0000` |                             |
| + | `0x4FFF FFFF` | `0x4FFF FFFF` | (last address of `Bank 1` ) |
|   | `0x5000 0000` | `0x5FFF FFFF` |                             |

Address `Bank 2` = `0x5000 0000` - `0x5FFF FFFF`

### Calculate `Bank 3` address range

$512\text{ MB} = 512 * 1\text{ MB} = 2^{log_2(512)} * 2^{20} = 2^9*2^{20} = 2^{(9+20)} = \\ 2^{29} = 536, 870, 912_{10} = \text{0x2000 0000}$

`0x0000 0000` - `0x5FFF FFFF` is taken, so add `0x5FFF FFFF` to the address range

|   | start         | end           |                             |
|---|---------------|---------------|-----------------------------|
|   | `0x0000 0001` | `0x2000 0000` |                             |
| + | `0x5FFF FFFF` | `0x5FFF FFFF` | (last address of `Bank 2` ) |
|   | `0x6000 0000` | `0x7FFF FFFF` |                             |

Address `Bank 3` = `0x6000 0000` - `0x7FFF FFFF`

### Answer

| Bank #   | Size   | Start Address | End Address   |
|----------|--------|---------------|---------------|
| `Bank 3` | 512 MB | `0x6000 0000` | `0x7FFF FFFF` |
| `Bank 2` | 256 MB | `0x5000 0000` | `0x5FFF FFFF` |
| `Bank 1` | 768 MB | `0x2000 0000` | `0x4FFF FFFF` |
| `Bank 0` | 512 MB | `0x0000 0000` | `0x1FFF FFFF` |

<table>
  <tr><td bgcolor="#e2efd9">0x7FFF FFFF<br/>Bank 3<br/>&nbsp; <br/>0x6000 0000</td></tr>
  <tr><td bgcolor="#a5a5a5">0x5FFF FFFF<br/>Bank 2<br/>0x5000 0000</td></tr>
  <tr><td bgcolor="#4672c4">0x4FFF FFFF<br/>&nbsp; <br/>Bank 1<br/>&nbsp; <br/>0x2000 0000</td></tr>
  <tr><td bgcolor="#fbe5d5">0x1FFF FFFF<br/>Bank 0<br/>&nbsp; <br/>0x0000 0000</td></tr>
</table>

Solution: built with [Memory layout diagrams](https://github.com/gerph/memory-layout-diagram "Memory layout diagrams")

![memory-map-3](image/memory-maps-exercises/memory-map-3.svg)

> [Image source code](image/memory-maps-exercises/memory-map-3.mld)

---
Copyright &copy; 2024 Mark Crowe <https://github.com/marcocrowe>. All rights reserved.
