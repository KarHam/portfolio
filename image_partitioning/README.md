This is my first serious attempt at machine learning; and I invented it in my senior high school year without any knowledge of ML, so it's of great sentimental value to me.

<h3>Task:</h3>

I wanted to partition images based on major sections, and realized that doing so would require analyzing relationships between colors and coordinates.
The algorithm I devised was fairly complicated, but was inspired by my fervent interest in biological evolution.


<h3>Algorithm:</h3>

A relation consists of 2 halves, the right half describes an area in the image, and the left half describes a color condition to be applied for this area.
We have building blocks, which are expressions like X<5, or R>56 where X is the x coordinate and R is the red color.
These blocks are combined using parenthesis and union/intersection operations. 
Ex: In a 200 x 200 image with R G B A system, the following relation:
 (G<20) and (B<20) and (R>133)K(X>133) 
Means that for the right third of the image, we need to see a mostly red bar. This relation would score highly on an Italian flag.
To evaluate expressions, we parse the expression and see whether the described areas in the image satisfy the described color requirements. (I wish I had known about antlr before I wrote my own parser) 
The score is a joint weighted metric of 
1) accuracy, or how much of the described area satisfies the color requirements
2) How much area is described (expressions that describe larger statements are favored) 
3) How specific the statement is (the less colors it accepts, the better)
The best expressions are taken, and true to the evolution spirit, are mutated, either gaining or losing building blocks. This goes on for a few iterations.
<h3>
Results:
</h3>

The best results are shown in the file. Highlighted regions correspond to areas that the relation for this image guessed correctly.
The algorithm did exceptionally well with images with straight lines, however due to the building blocks not supporting more complicated polynomial Y in terms of X,  the algorithm was doomed not to be able to recognize curves.
Another weakness was complexity and readability; I'm sure 8 nested loops were not a great idea in hindsight, and may be the reason why I remember letting the algorithm run for days.

<h3>
My take:
</h3>

Although the code is a slow mess, I’m very proud of this work; it exemplifies my work spirit: innovation irrespective of knowledge. Over my 3 years in CSE, I’ve become a competitive programmer, obsessed with optimality and speed of code, and I’ve learned several ML algorithms and their best practices, but true to my roots, I never turn down the unknown adventure when it shows up.
