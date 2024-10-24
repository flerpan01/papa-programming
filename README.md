# Papa programming

This repository holds a collection of coding puzzles together with my solutions using the programming language `R`. I see this as a fun and interactive way of becoming a better programmer. Feel free to join me!

For this we'll be using Github, Advent of Code and Rosalind. Advent of code contains general code puzzles while Rosalind contains bioinformatical code puzzles. Both are equal challenging!

### Preparations

Before we start, complete these tasks:

1. create an account on [github](https://github.com)
2. create an account on [advent of code](https://adventofcode.com) (here you can use your github login)
3. create an account on [rosalind](https://rosalind.info/) (here you can use your github login)

---

## First assignment

For the first puzzle we'll be using the [advent of code day 1 puzzle](https://adventofcode.com/2015/day/1), a perfect warm-up. Read and understand the problem, download the "floor directions", import them to `R`, write some script that makes sense of these "floor directions", solve the puzzle!

If you get stuck check the code below:

<details>

<summary>I'm stuck!</summary>

In order to solve this problem we need to understand some programming concepts: (1) vectors and (2) elements.

A `vector` is like a sentence, _"Hi, I like to swim and sunbath!"_, one dimentional. Reads right to left. Every step (or character) in a `vector` is an `element` and(!) has a unique adress:

```
$ Hi, I like to swim and sunbath!

elements H i , I l i k e t  o  s  w  i  m  a  n  d  s  u  n  b  a  t  h  !
adresses 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
```

>In some programming languages, like `python`, the first element starts with a `0`. Naturally, in `R`, the first element starts on `1`.

The first part of the puzzle requires us to:

1. Save the given vector. In order to follow the code below, be sure to save the vector as `advent_of_code_2015_day1.txt` inside a folder called `puzzle1`

```
# folder structure
project/
`-- puzzle1/
    `-- advent_of_code_2015_day1.txt
```

2. Open `R` / `Rstudio`, preferrably inside the `project/` folder, this will ensure the working directory is correct.
3. Inside R, import the text file

```r
# Import the text file
textfile <- readLines("puzzle1/advent_of_code_2015_day1.txt")

# inspect the variable textfile
print(textfile)

#> textfile
#[1] "()(((()))(((())(()(()((((((()(()(((( ... "
```

4. Currently, the the textfile is a very long string, a vector with one element (the string). To split up the string into elements use the function `strsplit()`

```r
vec <- strsplit(x = textfile, split = "")[[1]]

# inspect the vector
print(vec)
#[[1]]
#  [1] "(" ")" "(" "(" "(" "(" ")" ")" ")" "(" "(" ")" "(" ")" "(" ")" "(" "("
```

5. `strsplit()` return a list, either `unlist` or chose the first element in the list `[[1]]`

```r
# both gives the same result
#vec <- unlist(vec)
#vec <- vec[[1]]
```

6. In order to solve the puzzle and find the correct floor, replace the "(" with +1 and ")" with -1. For this use the function `gsub()`. `gsub()` basically means _global-substitution_ and replaces the give `pattern` with the `replacement` globally. Note, to tell R to find "(" we need to add two backslashes (`\\`) because `pattern` takes in a [regular expression](https://en.wikipedia.org/wiki/Regular_expression) and `\\` are read as escapes. This is because "(" and ")" are both use by regular expressions (more on that later).

```r
vec <- gsub(pattern = "\\(", replacement = 1, x = vec)
vec <- gsub(pattern = "\\)", replacement = -1, x = vec)

#head(vec)
#[1] "1" "-1" "1" "1" "1" "1"
```

7. Now, lets sum up this long vector and we should have the correct floor for santa

```r
# first make all the elements in the vector into numerical
vec <- as.numeric(vec)
floor <- sum(vec)

print(floor) # success
```

#### The final code

```R
textfile <- readLines("puzzle1/advent_of_code_2015_day1.txt")

vec <- strsplit(x = textfile, split = "")[[1]]
vec <- gsub(pattern = "\\(", replacement = 1, x = vec)
vec <- gsub(pattern = "\\)", replacement = -1, x = vec)

vec <- as.numeric(vec)
floor <- sum(vec)

print(floor)
```

</details>

<!--

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

-->