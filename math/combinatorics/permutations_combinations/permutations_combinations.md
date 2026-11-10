# Factorials, Permutations, and Combinations

[Back to Home](../../../README.md)


## Permutation of $n$ objects

You have been hired as an administrator at a school, and you're tasked with scheduling the lessons. For simplicity, each day is broken up into 4 periods, and you just have to schedule 4 subjects—biology, chemistry, physics, and history—for one day.

There are many ways to arrange this schedule, but how many are there exactly?

Let's call the total number of objects $n$. In this case, it is 4.

<img src="assets/1.jpg" width="500">

$$\text{Total options} = \underbrace{4}_\text{period 1} $$

Start with the first period. There are 4 possible subjects you can assign to it, so let's say you choose biology.

<img src="assets/2.jpg" width="500">

$$\text{Total options} = \underbrace{4}_\text{period 1} \times \underbrace{3}_\text{period 2}$$

Now, there are 3 subjects left you can assign to the second period. Therefore, looking at only the first two periods, there are $4 \times 3$ options.

You can picture this like a diverging path. At first, the path diverges into 4 (your choice for the first subject). And whichever one you follow will later diverge again into 3 (choosing the second subject).

<img src="assets/3.jpg" width="500">

$$\text{Total options} = \underbrace{4}_\text{period 1} \times \underbrace{3}_\text{period 2} \times \underbrace{2}_\text{period 3}$$

There will be 2 options left for the third period. Each path from before branches into 2, making the total number $4 \times 3 \times 2$.

<img src="assets/4.jpg" width="500">

$$\text{Total options} = \underbrace{4}_\text{period 1} \times \underbrace{3}_\text{period 2} \times \underbrace{2}_\text{period 3} \times \underbrace{1}_\text{period 4}$$

Finally, there is one option left to assign to the last period, which means we multiply by 1 at the end.

Try this same scenario but with different numbers. For example, assigning 6 subjects to 6 periods ($n = 6$). 

| Period | Options |
| :---: | :---: |
| 1 | 6 |
| 2 | 5 |
| 3 | 4 |
| 4 | 3 |
| 5 | 2 |
| 6 | 1 |

Notice the pattern here. When filling the first slot, there were $n$ options. Then, for each subsequent slot, the number of options lowers by 1. This repeats until the last slot, which always has 1 option.

The example we just analyzed involves **permutation**, the act of arranging objects in a specific order. And the calculation we discovered for calculating the number of permutations has a name, the **factorial**. It is written with an exclamation mark.

$$n! = n \times (n-1) \times (n-2) \times \cdots \times 3 \times 2 \times 1$$

This can be used in many different cases. Deciding the presentation order of students, arranging books on a shelf, shuffling a deck of cards, etc. The last example is quite infamous, because the number of ways to arrange a deck of cards ($52!$) is an unimaginably large number ([watch this YouTube short](https://youtube.com/shorts/L0nmxIQWefA?si=hoB8cJr2hfmuJrbY)).


## Permutation of $n$ objects out of $r$ total objects

The student council is holding an election. Who will win, Cole or Leo?? Who cares, because the event is going to take up the last 2 periods of the day, leaving 2 left for regular classes. With this extra constraint, how many permutations of the schedule are left?

$n$ is equal to 4, because there are still 4 subjects to choose from. However, we introduce a new variable, $r$, which represents how many of those subjects we can take. In this case, $r = 2$.

Start with $n!$ schedules containing $n$ periods (what we did before). Then, chop off the last $(n - r)$ periods from every possible schedule, leaving $r$ periods left in each.

<img src="assets/5.jpg" width="500">

We still have $n!$ schedules. But, you can see that the process left duplicate schedules, which shouldn't count as unique.

Think about why this happens. Looking at the two leftmost schedules for example, the only difference was in the permutation of the last $(n - r)$ subjects. But this disappears when you cut off the end of the schedule. 

Schedules that have the same first $r$ subjects and only differ in the last $(n - r)$ subjects end up being duplicates. 

Let's say we choose biology and chemistry to fill the first two periods. How many ways can the remaining two ($4-2$) subjects—physics and history—fit into the final two periods?

Using the formula from before, it is simply $2! = 2$ ways. This means that there are 2 schedules that start with biology then chemistry, and have the other two subjects in any order. But since the last two periods got cut off, we will just end up with 2 duplicate schedules containing bio and chem.

That's the key to solving our problem. Each unique schedule we are left with is repeated a total of 2 times (remember that 2 comes from $(4-2)!$), so we must divide the amount (24) by 2, giving us 12 as the final answer.

Generalizing this to any number of objects, we started with $n$ total objects, but only had to fill $r$ slots. To get the result, we must divide $n!$ by the number of times each permutation is duplicated, which is equal to the number of permutations of the objects that got cut off, $(n-r)!$. This operation is written in a few different ways:

$$_nP_r = \ ^nP_r = P(n, r) = \frac{n!}{(n-r)!}$$


## Combinations

Permutation is useful when order *does* matter, like when making a schedule. But for students packing their backpacks the day before, they simply need to know what subjects there will be, *not in what order*. In essence, you are simply choosing 2 subjects out of the 4.

So, if there are 4 subjects but only 2 periods, how many possible ways could a student need to pack their bag?

<img src="assets/6.jpg" width="500">

These are the 12 permutations from the previous section. Again, we must get rid of duplicates. For instance, biology-chemistry requires the same books as chemistry-biology.

Each unique combination is repeated twice, but think about where the number 2 comes from. 

Once you choose $r$ objects (the 2 subjects), there are $r! = 2! = 2$ ways to shuffle them in the schedule, which we must get rid of. Therefore, we divide 12 by 2, giving us 6 possible combinations (you can verify this manually).

In conclusion, the formula for the number of combinations is just the $_nP_r$ formula divided by $r!$. Again, this can be written in a few different ways, such as $_nC_r$, read as "$n$ choose $r$".

$$_nC_r = \ ^nC_r = C(n, r) = \binom{n}{r} = \frac{n!}{r!(n-r)!}$$


## Additional tips and tricks

### $$_nC_r = \ _nC_{(n-r)}$$
You can prove this pretty simply using the formula, but intuitively, it also makes sense. If you have 10 people and have to choose 8 from among them, it is the same as choosing 2 people to exclude.

### $$_nC_0 = \ _nC_n = 1$$
If you think about it, there is only 1 way to choose no one from a group of let's say 10 people, and there is also only 1 way to choose 10 people from 10 people.

### $$_nC_1 = \ _nC_{(n-1)} = n$$