# ontime

Punctual extensions

## ChronoHydra: a hydra that controls time and is therefore always punctual.

import "https://ontime.savamala.top/chronohydra.punctual";

This is a reimplementation of some Hydra Synth functions in Punctual.

There are some key difference between the original functions and this version:

- The names are generally shorter, to be consistent with Punctual naming. aesthetics.
- There are generally fewer arguments. This is because functions in Punctual doesn't have optional parameters, so one would be forced to type all the parameters each time. Also, the effects of many parameters are easily mimicked in Punctual using simple operations.
- There are some changes in the geometry, as Punctual uses a -1 to 1 coordinate range with (0,0) at the center, while Hydra uses a 0 to 1 coordinate range with (0,0) at the top-left corner.

Functions in ChronoHydra:

- `hosc freq offset`

`hosc` is Hydra's `osc` (the change in naming is to avoid collision with the Punctual function named also `osc`). `sync` argument has been removed, as it can be easily replicated with `move`.

Example:

```
move [saw (-0.3),0] $ hosc 200 0.5
```

- `hoscp freq offset`

Non-combinatorial version of `hosc`.

- `shape sides radius smoothing`

`radius` and `smoothing` are halved compared to those on Hydra, to adapt to Punctual's geometry.

`shape 4 0.5 0` is equivalent to `rect 0 [0.5,0.5]`

- `shapep`

Non-combinatorial version of shape.

- `star sides radius smoothing`

`star` (doesn't exist in hydra) is a variation on `shape` that draws stars instead of regular polygons.

- `starp`

The non-combinatorial version of `star`.

- `stard sides smoothing deepness`

Removes the `radius` argument (takes 1) and introduces `deepness`, which indicates how deep the cuts in the original shape are.

- `stardp`

The non-combinatorial version of `stard`.


- `kaleid nSides`

Equivalent to Hydra's `kaleid`, except it takes the image to repeat from the center, not from the top left side.
