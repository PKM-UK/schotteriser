To create geometry in the drawing, add a generator. These draw shapes in a repeating pattern: grid, circle, spiral etc. with customisable position and spacing.  Multiple different generators can be used in a single scene and their output will be combined together. The shapes are "hollow" with no fill as this output is intended to be used with pen plotters and similar devices. ![Alt text](/docs/scdocs2.JPG?raw=true)

To modify the geometry in the drawing, you can then add transforms to the pipeline. Transforms will move, rotate or scale shapes based on their position in the drawing between specified limits. In this example the hearts and arrows are moved downwards based on their X coordinate.
![Alt text](/docs/scdocs3.JPG?raw=true)

Multiple transforms may also be used - their effects will be applied in order, so earlier transforms may affect the result of later ones. In this example the hearts which were moved further down the drawing are affected more by the following scale transform. ![Alt text](/docs/scdocs4.JPG?raw=true)

If a transform is randomised, its effect on each shape will be randomly chosen somewhere between the minimum transform value and the amount it would normally affect that shape by.
![Alt text](/docs/scdocs5.JPG?raw=true)![Alt text](/docs/scdocs6.JPG?raw=true)

A transform can be given a random sign, which means the effect will randomly (p=0.5) be applied in the opposite direction. ![Alt text](/docs/scdocs7.JPG?raw=true) These options can be combined for a transform with a random amount and random direction.

Specifying a number of steps will cause the effect to "snap" to the nearest one of the specified number of steps between the minimum and maximum values inclusive. ![Alt text](/docs/scdocs8.JPG?raw=true)

Lets use these to recreate two classic algorithmic designs: Schotter and 10 PRINT

Create a grid of squares 12 across by 18 rows high. The squares should be tightly packed so we set the size ![Alt text](/docs/scdocsradius.JPG?raw=true) to 5 and the spacing to 10.
![Alt text](/docs/scdocs9.JPG?raw=true)

A rotate in place transform with a random, bidirectional effect from 0 to 45 degrees increasing as the squares get further down the drawing creates the random angle jitter of the original. ![Alt text](/docs/scdocs10.JPG?raw=true)

The squares are also displaced from their starting positions in the original so we need to add a random bidirectional x translate and y translate based on the Y coordinate. ![Alt text](/docs/scdocs11.JPG?raw=true)

To recreate 10 PRINT, we just need a grid of short line segments rotated clockwise or anticlockwise by 45 degrees. There are a couple of ways we could accomplish this: either by adding a constant rotation between -45 and 45 degrees, randomised with two steps ![Alt text](/docs/scdocsso each line is either rotated -45 or +45 degrees.JPG?raw=true), or by using a constant 45 degree rotation with a randomised direction. ![Alt text](/docs/scdocs12.JPG?raw=true)