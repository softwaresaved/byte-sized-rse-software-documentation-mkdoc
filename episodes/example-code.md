---
title: "Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a minimum documentation needed for people to be able to reuse some else's code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Obtain and run example code used for this lesson
- List documentation types missing from the example code

::::::::::::::::::::::::::::::::::::::::::::::::

## Obtaining Example Code

For this lesson we'll be using some [example code that does spacewalks analysis](https://github.com/softwaresaved/spacewalks) available on GitHub, which we'll clone onto our machines using the Bash shell.
The spacewalks code is available from:

`https://github.com/softwaresaved/spacewalks`.

Firstly, create your own copy of the spacewalks repository that you can commit to by using `Use this template` button on GitHub.

Then, open a command-line shell (e.g. via Git Bash in Windows, bash shell on Linux or Terminal on a Mac) and navigate to where you would like the example code to reside (e.g. to your home directory).

Use Git to clone your copy of the spacewalks repository.

```bash
cd
git clone https://github.com/your-repository/spacewalks.git
cd spacewalks
```

::::::::::::::::::::::::::::::::::::::::: instructor

## Checkpoint: Attendee Progress

Who's been able to clone the GitHub repository on their local machine?

:::::::::::::::::::::::::::::::::::::::::


## Examining the Code

Let's take a look at the spacewalk analysis code, which is in the root directory of the repository in a file called `eva_data_analysis.py`.
Feel free to use your preferred editor of choice, such as Notepad, Nano or Visual Studio Code.

The code is designed to:

- Read in the data from the JSON file
- Change the data from one data format to another and saves to a file in the new format (CSV)
- Perform some calculations to generate summary statistics about the data
- Make a plot to visualise the data

A few things to note about the code:

- it contains `requirements.txt` file listing its dependencies - Pandas, Pytest, Matplotlib to name a few
- it already contains comprehensive docstrings comments
- it contains the `tests` folder with tests
- it contains `data` folder with input data and `results` folder where it saves data converted to CSV format and the resulting plot


## Running the Example Code

Let's see if the code runs.

Firstly, we will install the necessary dependencies:

```
python3 -m pip install -r requirements.txt
```

Note: some users may be able to just use the `python` command instead of `python3`.
We are using `python3` just to be on the safe side.

To ensure the code is working correctly, run the tests using Pytest.

```
python3 -m pytest
```

To run the analysis using the `eva_data_analysis.py` script from the command line terminal, do:

```
python3 eva_data_analysis.py data/eva-data.json results/eva-data.csv
```

If the code runs successfully, you should get the resulting plot in results/cumulative_eva_graph.png


::: challenge

## What documentation for this software is missing?

Would you be able to figure out how to run the code on your own?

::: hint
 
- Would you be able to figure out how to run the code on your own?

:::

:::

::::::::::::::::::::::::::::::::::::: keypoints 

- Minimum information needed to run someone else code should include the purpose of the code, installation and setup instructions (including dependencies), and usage example (how to run the code).

::::::::::::::::::::::::::::::::::::::::::::::::
