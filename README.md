# Papa programming

We'll be using github, advent of code and rosalind. Advent of code contains general code puzzles. Rosalind contains bioinformatical code puzzles. Both are equal challenging!

Lets get to work. First, complete the tasks below:

1. create an account on [github](www.github.com)
2. create an account on [advent of code](www.adventofcode.com) (here you can use your github login)
3. create an account on [rosalind.info](https://rosalind.info/) (here you can use your github login)

---

+ I'll be using R

## First assignment

For the first puzzle we'll use the [advent of code day 1 problem](https://adventofcode.com/2015/day/1), this will be a perfect warm-up. 

In order to solve this problem we need understand some programming concepts: (1) vectors & (2) elements.

A `vector` is like a sentence, "Hi, I like to swim and sunbath!", one dimentional: reads right to left. Every step or character is an `element` and has a unique adress:

```
$ Hi, I like to swim and sunbath!

vector   H i , I l i k e t  o  s  w  i  m  a  n  d  s  u  n  b  a  t  h  !
adresses 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
```

>In some programming languages, like `python`, the first element starts with a `0`. In `R`, the first element starts on `1`

```r
# Import the text file
textfile <- readLines("puzzle1/advent_of_code_2015_day1.txt")


vec <- strsplit(textfile, "")[[1]]
vec <- gsub(pattern = "[(]", replacement = 1, x = vec)
vec <- gsub(pattern = "[)]", replacement = -1, x = vec)
vec <- as.numeric(vec)
floor <- sum(vec)

print(floor)
```

```r
# we start on floor number 0
floor <- 0

for ( index in seq_along(vec) ){
  floor <- vec[index] + floor

  if ( floor == -1 ) {
    print(index)

    # we found our index, we can not stop the for loop earlier
    break
  }
}
```



+ papa-programming
  + first assignment
  + quarto sida per problem? 
  + [githubaction renderar html](https://github.com/quarto-dev/quarto-actions)
