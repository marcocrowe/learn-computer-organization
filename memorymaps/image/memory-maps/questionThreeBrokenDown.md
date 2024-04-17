# memory map for question 3

## Bank 0 = 512mb

536,870,911 = available addresses available for bank 0

    536,870,911
Bank 0 = 0000 0000 -> 1FFF FFFF

## Bank 1 = 768mb

1,342,177,279 - 536,870,911 = 805,306,368 possible addresses available for bank 1

    1,342,177,279
Bank 1 = 2000 0000 -> 4FFF FFFF

## Bank 2 = 256mb

1,610,612,735 - 1,342,177,279 = 268,435,456 possible addresses available for bank 2

    1,610,612,735
Bank 2 = 5000 0000 -> 5FFF FFFF

## Bank 3 = 512mb

2,147,483,647 - 1,610,612,735 = 536,870,912 possible addresses available for bank 3

    2,147,483,647

Bank 3 = 6000 0000 -> 7FFF FFFF
