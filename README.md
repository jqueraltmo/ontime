# ontime

Punctual extensions

## ChronoHydra: a hydra that controls time and is therefore always punctual.

```
import "https://ontime.savamala.top/chronohydra.punctual";
```

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

## Usual: functions that I usually use inside Punctual

```
import "https://ontime.savamala.top/usual.punctual";
```

- `rgbrbg`, `rgbbgr`...

Reorder a 3-channel signal.

- `mover`, `moveg`, `moveb`

Move only one of the three channels.

- `cmix c1 c2`

A subtractive color mixing function.

- `black`, `white`, `red`, `lime`...

A list of colors.

- `mirrorx pos l`, `mirrory`, `mirrorxy`

Creates a mirroring effect with repetitions. Inspired by @GEIKHA's `hydra-fractals`.

`mirrorx 0.4 0.3 graph` creates a mirror at x=0.4, repeating every 0.3 units.

- `movex dx`, `movey dy`

Shortcuts for `move [dx,0]` and `move [0,dy]`.

- `spin2 x`

Shortcut for `spin [x, (-1)*x]`.

- `inv x`

Shortcut for `1-x`.

- `onceosc f`

An oscillator that runs only once, starting at 0 when the expression is executed.
