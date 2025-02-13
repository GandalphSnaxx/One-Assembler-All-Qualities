# One-Assembler-All-Qualities
A [Factorio](https://factorio.com/) blueprint book containing assemblers that can produce any and every quality items in a compact form factor. Module variations allow the user to specify the quantity of each or every item quality these modules should store. This repository was created with the help of [FaTul](https://github.com/nyurik/fatul#factorio-blueprint-git-tool-fatul)
**Buildings with built in 50% productivit have their productivity accounted for! Get 3 products for the price of 2!**

![The one assembler that makes all the qualities.](/Images/assembler.jpg)

## Usage:

### Standard usage
1. Choose which building to use
2. Set the parameterized item and buffer limits
3. Set the unlocked qualities in the constant combinator

### Edge case usage
- Each entity can be upgraded to a better quality
- Each quality module can be replaced by a higher quality module
- If the number of buffer stacks exceeds the limit of the buffer chest, replace the buffer chest with a higher quality buffer chest
    *At least one chest slot must remain empty so ingredients can be removed from the assembler*
- If the number of requested ingredient stacks exceeds the limit of the requester chest, replace the requester chest with a higher quality requester chest
    *This can happen with recipes such as the rocket silo or mech armor*

## Variants

There are four main variants of this design: **Set Each Stack**, **Set Every Stack**, **Decreasing Stacks,** and **Ray's Preferred Stacks**. Each variant lets the user change the buffer limit of quality products in different ways.
- **Set Each Stack**: Each product quality can have different buffer limits.
    - Buffer limit example: 5 Normal Stacks, 0 Uncommon Stacks, 3 Rare Stacks, 1 Epic Stack, and 0 Legendary Stacks
- **Set Every Stack**: Every product quality has the same buffer limit.
    - Buffer limit example: 2 Normal Stacks, 2 Uncommon Stacks, 2 Rare Stacks, 2 Epic Stack, and 2 Legendary Stacks
- **Decreasing Stacks**: You set the buffer limit of normal quality products and each rarer quality has its buffer limit set to half the number of stacks of the previous rarity.
    - Buffer limit example: 16 Normal Stacks, 8 Uncommon Stacks, 4 Rare Stacks, 2 Epic Stacks, and 1 Legendary Stack
- **Ray's Preferred Stacks**: Similar to Decreasing Stacks, but uncommon items only get one stack buffered. Rare products get half the buffer size of normal.
    - Buffer limit example: 16 Normal Stacks, 1 Uncommon Stack, 8 Rare Stacks, 4 Epic Stacks, and 2 Legendary Stacks

## Upgrading

Each building can be replaced by a building of higher quality as long as they have the same base productivity. Each module can be replaced by a quality module of higher quality. Each recycler can be replaced by a recycler of higher quality. Each inserter can be replaced by a better inserter or an inserter of higher quality. If you really want, each combinator can be replaced with a combinator of higher quality too...

## Blueprint Book Directory

- One Assembler, All Qualities<br/>*Main blueprint book*
    - [x] Set Each Stack<br/>*FINISHED. Allows the user to set the number of stacks to buffer of each quality product*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
    - [x] Set Every Stack<br/>*FINISHED. Allows the user to set the number of stacks to buffer of every quality product*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
    - [x] Decreasing Stacks<br/>*FINISHED. Set the number of normal quality products to buffer and each higher quality product will have half the buffer of the quality before it*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
    - [x] Ray's Preferred Stacks<br/>*FINISHED. Set the number of normal stacks then buffer each higher quality in Ray's preferred quantities*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
    - [ ] Include Heat Pipes<br/>*TODO! Heat pipes are included for use on Aquillo. These are modified versions of the **Set Each Buffer** modules*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
    - [x] Backups<br/>*FINISHED. Backups of each assembly building*
        - Assembler 3
        - Chemical Plant
        - Cryogenic Plant
        - Biochamber
        - Electromagnetic Plant
        - Foundary
        - Assembler 3 with no parameter functions
        - Just the circuitry

## Included Buildings

### Assembler 3
![Assembler 3 module](/Images/assembler.jpg)

### Chemical Plant
![Chemical plant module](/Images/chem_plant.jpg)

### Cryogenic Plant
![Cryogenic plant module](/Images/cryo_plant.jpg)

### Biochamber
![Biochamber module](/Images/biochamber.jpg)

### Electromagnetic Plant
![Electromagnetic plant module](/Images/em_plant.jpg)

### Foundary
![Foundary module](/Images/foundary.jpg)

## How This Works

The heart of the design is the four single combinator Set/Reset (SR) latches deciding when to request a higher quality recipe. The set conditions check the number of ingredients, buffer status, and other recipe requests. The reset condition checks for a *craft done* pulse and other recipe requests. Another combinator requests the normal recipe when no higher quality recipe is requested and any buffer is not full. The final combinator translates the buffer status to a binary value and forwards the *quality enable* signals to the SR latches.

## Other Information

At some point, I realized adding this many conditions to a combinator on top of filling its description box was going to result in a very large blueprint string for such a small blueprint. I am quite happy with how it turned out but now I am beginning to wonder how dense can a blueprint be.
Please share this design with your friends, I would like to see this design on someone's lets-play one day!
If people wish for a more in-depth explanation of how this design works, I can make a video explanation if I get enough requests!

## TODO:
- [ ] Design variants with heat pipes for Aquilo<br/>*Space out combinators and move the buffer chest to make room for heat pipes*
- [ ] Add handling of 0 stack buffers<br/>*Set the number of items to buffer to -1 in the constant combinator if 0 stacks should be buffered*
- [ ] Add modules for other buildings
- [ ] Update the GitHub repo
    - [ ] Add pages to explain what each entity does
    - [ ] Add markups to each entity image
    - [ ] Link explinations to the directory