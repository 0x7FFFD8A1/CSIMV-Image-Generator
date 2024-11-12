# CSIMV-Image-Generator
_Cosine Similarity Vector Generator._\
A new way to look at mathematically generated images using the analyzation \
of the similarities and differences between pairs of pixels.

Its alright as a stupid little gimmick, but its pretty irrelevent in today's world. \
If you don't know why, search up 'DALL-E' in your browser of choice

__please note that the final output images have been edited for clarity__ \
_contrast and sharpness has been increased._

_this project is featured in Code-02_

#### Equation Functionality
It works by finding the cosine similarities of pixels sorted into pairs.
```
              a⋅b
sim(a, b) = -------
            |a|*|b|

a⋅b = Dot product of vector a and b
|a| = Euclidean norm of vector a
|b| = Euclidean norm of vector b
```
Then it converts the end result into a vector.
```
     [ sim(ab) ]
     [    1    ]
 v = [    1    ]
     [   ...   ]
     [    1    ]
```
After this has been completed, it takes a pair of \
these vectors and finds its midpoint.
```
M = ((x₁ + x₂) / 2, (y₁ + y₂) / 2)
```
Finally, it calculates the properties of the final \
midpoint vector
```
Magnitude: ||v|| = √(v1² + v2² + ... + vn²)
Direction: θ = arctan(y/x)
```
These values are used in the calculation of the blue value, \
whilst the vector is used for red and green values

#### Conversions
- Pixels are converted to UINT8 for compatibility.
- Magnitude is used in the blue values, but after testing, it has \
  been found that Direction is not efficient for calculating alpha values.
- Magnitude is used as a property to compair pixels

#### Decoding
2 Planar vectors (with 1 as a filler) are plotted on a virtual \
2 dimensional plane in a straight line. Then, using the midpoint formula, \
the planar coordinate for the center of the line is found.
This final vector is appended to the final pixel image \
(x, y contributes to r, g respectively)

The straight line is calculated as a linear gradient with options to \
interpret it with either the mean of the two vectors or a singular \
midpoint formula as mentioned above.
