# Plagiarism Detection

The aim of this project is to devise a plagiarism detection algorithm that will sufficiently detect aims to plagiarise the content. While no detection is perfect and there are always some [innovative ways](https://spinbot.com/) to fight the plagiarism, we aim to design a method that will render fighting the plagiarism detection engine more resource demanding than actually creating the solution.

We are designing this system as part of our [Clara World](https://claraworld.net/) system. The unique advantage of our system is the fact that we save every single change in code that a student is producing, allowing us to re-construct the whole assignment creation process.

# The Idea

The original idea from the [support ticket](https://github.com/tomitrescak/clara-support/issues/66) is to detect significant increments in submitted code to detect the plagiarism. This leads to to our first hypothesis.

**H1: If a student submits more than 80% of the solution in one delta leads to suspected plagiarism**

Already, we suspect that for simple solutions we will receive a lot of false positive

# Project Diary

- 02/02/2022 - Starting to work on the [support ticket](https://github.com/tomitrescak/clara-support/issues/66) that proposes a simple plagiarism detection text
- 07/02/2022 - Contacted the Ethics Committee for permission to work on this project
- 07/02/2022 - Obtained a list of plagiarism cases from 2015
