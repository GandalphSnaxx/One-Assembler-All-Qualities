# One-Assembler-All-Qualities
A [Factorio](https://factorio.com/) blueprint book containing assemblers that can produce any and every quality items in a compact form factor. Module variations allow the user to specify the quantity of each or every item quality these modules should store. This repository was created with the help of [FaTul](https://github.com/nyurik/fatul#factorio-blueprint-git-tool-fatul)\
![The one assembler that makes all the qualities.](/Images/assembler.jpg)
Buildings with built in productivity is accounted for! Get 3 products for the price of 2!\
EDIT 0.5.1rc1: Removed the buildings that should be removed after placing a blueprint
## Usage:

1. Choose which building to use
2. Set the parameterized item and buffer limits
3. Set the unlocked qualities in the constant combinator

## Variants

There are four main variants of this design: **Set Each Stack, Set Every Stack, Decreasing Stacks,** and **Ray's Preferred Stacks**. Each variant changes the buffer limit of items produced in the assemblers.
- **Set Each Stack**: Each product quality can have different maximum buffer sizes.\
Ex: 5 Normal Stacks, 0 Uncommon Stacks, 3 Rare Stacks, 1 Epic Stack, and 0 Legendary Stacks
- **Set Every Stack**: Every product quality has the same buffer size. You only have to set one number!
- **Decreasing Stacks**: You set the number of normal quality stacks to buffer, and each rarer quality has its buffer limit set to half the number of stacks of the previous rarity or 1 stack.\
Ex: 16 Normal Stacks, 8 Uncommon Stacks, 4 Rare Stacks, 2 Epic Stacks, and 1 Legendary Stack
-**Ray's Preferred Stacks**: Similar to Decreasing Stacks, but uncommon items only get one stack buffered, and rare products get half the buffer size of normal.\
Ex: 16 Normal Stacks, 1 Uncommon Stack, 8 Rare Stacks, 4 Epic Stacks, and 2 Legendary Stacks
## Upgrading
Each building can be replaced by a building of higher quality as long as they have the same base productivity. Each module can be replaced by a quality module of higher quality. Each recycler can be replaced by a recycler of higher quality. Each inserter can be replaced by a better inserter or an inserter of higher quality. If you really want, each combinator can be replaced with a combinator of higher quality too...

## Blueprint Book Directory



## How This Works

The heart of the design is the four single combinator Set/Reset (SR) latches deciding when to request a higher quality recipe. The set conditions check the number of ingredients, buffer status, and other recipe requests. The reset condition checks for a *craft done* pulse and other recipe requests. Another combinator requests the normal recipe when no higher quality recipe is requested and any buffer is not full. The final combinator translates the buffer status to a binary value and forwards the *quality enable* signals to the SR latches.

## Other Information

At some point, I realized adding this many conditions to a combinator on top of filling its description box was going to result in a very large blueprint string for such a small blueprint. I am quite happy with how it turned out but now I am beginning to wonder how dense can a blueprint be.
Please share this design with your friends, I would like to see this design on someone's lets-play one day!
If people wish for a more in-depth explanation of how this design works, I can make a video explanation if I get enough requests!

## TODO:
- [] Design variants with heat pipes for Aquilo
- [] Add handling of 0 stack buffers
- [] Update the GitHub repo