# math-problem-generator

`math-problem-generator` is command-line tool that generates a set of randomized math problems, including right and wrong answers, in various categories (arithmetic, algebra, geometry, mathematical word problems, etc.), with the ability to output the generated problems in various formats (direct-to-screen, CSV file, etc.)

## Background

The non-profit organization [Jalawelo](https://www.jalawelo.org) (_Jamaica Land we Love_) is currently working to develop online math tests designed to prepare individuals in Jamaica for the [City & Guilds](https://www.cityandguilds.com) (C & G) _Certificate in Mathematics_ exams, part of City & Guilds' [Mathematics and English Skills (3850)](https://www.cityandguilds.com/qualifications-and-apprenticeships/skills-for-work-and-life/english-mathematics-and-ict-skills/3850-mathematics-and-english-skills#tab=information) qualification program.

These online tests are currently developed and maintained by hand. This requires a non-trivial investment in both time and resources, including: creating test questions according to the C & G math certification requirements, categorizing questions using the C & G exam stage schedule and criteria, reviewing and verifying test questions, and becoming well-versed in how to use the learning management system where online math tests are posted.

The `math-problem-generator` project aims to automate the creation of questions for these online math tests to save time and effort and reduce the risk of human error and the need for review and verification of test content.

## Design

### Problem Generators

The program uses _problem generators_ to generate problems. A _problem generator_ is a piece of code that can generate a specific type of math problem, but generate a slightly different variation of the problem each time it's used. This allows the `math-problem-generator` program to generate a different (and randomized) set of questions each time it is used.

For example, a "simple addition" problem generator might generate problems such as **What is 2 + 57?** and **What is 109 + 18?**, while a "algebraic equation" problem generator might produce **Find the value of X in the expression **Find the value for X if 29 ÷ X × 4 × 21 + 34 = 440** as well as **Find the value for X if 72 - 98 - 12 + 73 + X = 40**.

A problem generator produces a randomized problem statement within a given class of problem (i.e. **What is 2 + 57?**), the correct solution to the problem, and 3 incorrect (but reasonable) solutions. Including the correct solution along with a set of incorrect solutions makes the output suitable for both fill-in-the-blank and multiple-choice tests.

A problem generator may be fairly generic, such as the "simple addition" generator, or very specific, such as a problem generator that generates a randomized bar chart and asks which value represented in the chart is the largest.

Some problem generators may produce text-only problems and answers, while others may produce images for either the question or the answers, while others may produce a combination of text and images: the ability to create images is necessary for certain classes of problems, such as geometry problems, or problems involving complex equations that can't be easily expressed with simple text.

This approach (generating problems with the correct and incorrect solutions) also makes the output of the program usable as input for learning management systems, which can then present the problems in the form of an online test.

### Formatters

The program uses _formatters_ to produce output in different formats. A _formatter_ takes as input a list of problems generated by one or more problem generators, and produces a specific representation of those problems.

Some formatters may support text-only problems, while others may allow problems that contain images. This is because images may not make sense for all output formats. The program will produce an appropriate error message to the user if a formatter that doesn't support images is used to format problems that contain images.

The current version supports a single formatter that produces the CSV file format used to import questions into the [Easy LMS](https://easy-lms.com) learning management system (LMS), which is the online LMS currently used by Jalawelo to create online math tests.

More formatters may be added in the future.

### Command Line Interface

`math-problem-generator` is a command-line tool, and provides flexibility for users in how it generates problems and in the output it produces.

When it is run, it uses a set of _problem generators_, specified by the user, to generate a series of test questions (the number of questions to generate is also configurable), which it then outputs according to the options provided by the user.

## Contributing

This project is written in Python and Python 3.6 or newer is needed in order to work wih the code. Code contributions will only be accepted via [pull requests](https://help.github.com/en/articles/about-pull-requests) and will be merged pending review and approval by the project maintainers (@mgspross and @newoga). Contributors may be asked to make changes to their code in order for it to be merged.

A `CONTRIBUTING.md` document with more information on contributing to this project is currently being worked on (see issue #2).
