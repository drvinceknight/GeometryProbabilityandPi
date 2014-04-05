Repo containing resources for an outreach activity aiming to use dice to get an estimate for pi.

# Requirements:

Sufficient copies of the grid.pdf file and ten sided dice (depending on numbers students can be pairs).

# Instructions

The activity starts with a rather cryptic set of instructions:

1. Roll dice so as to obtain random coordinates for 10 points;
2. Place these points on the grid (don't worry where they go in the boxes);
3. Count the points that sit within the circle and perform the requested calculations.

Once this is done, ask the students what values they have obtained and if they know what this might be about?

Keep track of the numbers of the board and finally carry out a calculation over the total number of points.

# Explanations

As a group explain that probability of any given point landing in the circle is given by:

\[P(\text{point in circle})=\frac{\text{Area of circle}}{\text{Area of square}}\]

If we let \(r\) denote the radius of the circle this gives:

\[P(\text{point in circle})=\frac{\pi r^2}{(2r)^2}=\frac{\pi}{4}\]

Our data however gives us an **estimate** of \(P(\text{point in circle})\):

\[P(\text{point in circle})\approx frac{n}{N}\]

Thus we have:

\[\pi\approx 4\frac{n}{N}\]

At this point ask if what would make the experiment everyone did better? (Answer: more data).

# Code

Ideally some students might realise that another approach to doing this would be to get a computer to calculate this for us.
The following is some [Sage](http://sagemath.org/) code that will simulate the points and plot them as well:

    def simpoints(N=1000):
        points = [[random(), random()] for k in range(N)]
        pointsincircle = [k for k in points if k[0] ^ 2 + k[1] ^ 2 <= 1]
        p = list_plot(pointsincircle, color='blue')
        p += list_plot([k for k in points if k not in pointsincircle], color='black')
        p.show()
        return 4 * len(pointsincircle) / N
