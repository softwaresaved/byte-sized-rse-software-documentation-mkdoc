---
title: "Generating documentation with MkDocs"
teaching: 15
exercises: 45
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can we use tools like MkDocs to create documentation websites for our software?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Generate and manage comprehensive software documentation using MkDocs

::::::::::::::::::::::::::::::::::::::::::::::::

## MkDocs documentation tool

MkDocs is a static site generator tool that can be used to generate documentation website for software projects.
MkDocs builds standard static HTML files as its output which you host anywhere, for example on GitHub Pages or GitLab or any other website hosting platform.

At its core, MkDocs simply turns your Markdown files into a static website.
You can write Markdown files manually for any project, regardless of the language it is built in.

If you want to automatically generate documentation from your code's docstrings, you will also need the `mkdocstrings` plugin. 

MkDocs is written in Python and requires Python to run the `mkdocs` commands but you can use MkDocs to create documentation for software projects written in a number of programming language (as long as there is a handler for it).
Currently, there are `mkdocstrings` handlers for the C, Crystal, GitHub Actions, Python, MATLAB, TypeScript, and VBA languages, as well as for shell scripts/libraries.

## Installing MkDocs

Within an active virtual environment, do:

```bash
python3 -m pip install mkdocs
python3 -m pip install "mkdocstrings[python]"
python3 -m pip install mkdocs-material
```

Let's creates a new MkDocs project in the root of the spacewalks directory by running the `mkdocs` "new" command:

```bash
mkdocs new .    
```

```output
INFO    -  Writing config file: ./mkdocs.yml
INFO    -  Writing initial docs: ./docs/index.md
```

This command creates a new MkDocs project in the current directory with a `docs` folder containing an `index.md` file and a `mkdocs.yml` configuration file in the root of our project.

Now, let's fill in the `mkdocs.yml` configuration file for our project.

```yaml
site_name: Spacewalks Documentation
use_directory_urls: false
theme:
  name: "material"
  font: false
nav:
  - Spacewalks Documentation: index.md
  - Tutorials: tutorials.md
  - How-To Guides: how-to-guides.md
  - Reference: reference.md
  - Background: explanation.md
```

Note `font: false` variable is for GDPR compliance; `use_directory_url: false` variable tells MKDocs tools how to handle URLs for documentation that is served as a website (we will cover this in a moment).

Let's add support for `mkdocstrings` - this will allow us to automatically add our docstrings into our documentation using a simple tag.

```yaml
site_name: Spacewalks Documentation
use_directory_urls: false
theme:
  name: "material"
  font: false
nav:
  - Spacewalks Documentation: index.md
  - Tutorials: tutorials.md
  - How-To Guides: how-to-guides.md
  - Reference: reference.md
  - Background: explanation.md

plugins:
  - mkdocstrings
```

Let's populate our `docs/` folder to match our configuration file.

```bash
touch docs/tutorials.md
touch docs/how-to-guides.md
touch docs/reference.md
touch docs/explanation.md
```

Let's populate our reference file `reference.md` with some preamble to include before the reference manual that will be generated from the docstrings we created.

```markdown
This file documents the key functions in the Spacewalks tool.
It is provided as a reference manual.

::: eva_data_analysis

```

Finally, let's build our documentation.

```bash
mkdocs build
```

```output
INFO    -  Cleaning site directory
INFO    -  Building documentation to directory: /Users/AnnResearcher/spacewalks/site
WARNING -  griffe: eva_data_analysis.py:105: No type or annotation for returned value 'int'
WARNING -  griffe: eva_data_analysis.py:84: No type or annotation for returned value 1
WARNING -  griffe: eva_data_analysis.py:33: No type or annotation for returned value 1
INFO    -  Documentation built in 0.31 seconds
```

Once the build step is completed, our documentation site is saved to a `site` folder in the root of our project folder.
These files will be distributed with our code. 
We can either direct users to read these files locally on their own device using their browser, or we can choose to host our documentation as a website that our uses can navigate to.

Note that we used the setting `use_directory_urls: false` in the `mkdocs.yml` file. 
This setting ensures that the documentation site is generated with URLs that are easy to navigate locally on a user's device.

::: challenge

### Explore your documentation (5 min)

Explore documentation in `site/` folder built with MkDocs for your project, starting from the `index.html` file.

Open `index.html` file in a Web browser to see how it renders.

Check `site/reference.html` to see how docstrings from your functions are provided here as a reference manual.

:::

Finally, let us commit our documentation to the main branch of our Git repository and push the changes to GitHub.

```bash
git add mkdocs.yml 
git add docs/
git add site/
git commit -m "Add project-level documentation"
python3 -m pip freeze > requirements.txt
git add requirements.txt 
git commit -m "Added mkdocs plugin"
git push origin main
```

::::::::::::::::::::::::::::::::::::: callout

### Hosting documentation

We saw how MkDocs documentation can be distributed with our repository and viewed "offline" using a Web browser.

We can also make our documentation available as a live website by deploying our documentation to a hosting service.

:::::: spoiler

### Some options for hosting documentation

### GitHub Pages

As our repository is hosted in GitHub, we can use GitHub Pages - a service that allows GitHub users to host websites directly from their GitHub repositories.

There are two types of GitHub Pages: project pages and user/organization Pages.
While similar, they have different deployment workflows, and we will only discuss project pages here. 
For information about deploying to user/organisational pages, see [MkDocs Deployment pages][mkdocs-deploy].

Project Pages deploy site files to a branch (by default the `gh-pages` branch, but it can be any other branch) within the project repository. 
To deploy your documentation:

> **Warning!**
> Before we proceed to the next step, we MUST ensure that there are no uncommitted changes or untracked files in
> our repository.
>
> If there are, the commands used in the upcoming steps will include them in our documentation!

1. (If not done already), let us commit our documentation to the main branch of our Git repository and push the changes to GitHub.

```bash
(venv_spacewalks) $ git add mkdocs.yml 
(venv_spacewalks) $ git add docs/
(venv_spacewalks) $ git add site/
(venv_spacewalks) $ git commit -m "Add project-level documentation"
(venv_spacewalks) $ git push origin main
```

2. Once we are on the main branch and all our changes are up to date, run the following command from the command line terminal to deploy our documentation to GitHub.

```bash
# Important: 
# - This command will push the documentation to the gh-pages branch of your repository
# - It will ALSO include uncommitted changes and untracked files (read the warning above!!) <- VERY IMPORTANT!!
(venv_spacewalks) $ mkdocs gh-deploy
```

```output
INFO    -  Cleaning site directory
INFO    -  Building documentation to directory: /Users/AnnResearch/spacewalks/site
WARNING -  griffe: eva_data_analysis.py:105: No type or annotation for returned value 'int'
WARNING -  griffe: eva_data_analysis.py:84: No type or annotation for returned value 1
WARNING -  griffe: eva_data_analysis.py:33: No type or annotation for returned value 1
INFO    -  Documentation built in 0.37 seconds
WARNING -  Version check skipped: No version specified in previous deployment.
INFO    -  Copying '/Users/AnnResearcher/spacewalks/site' to 'gh-pages' branch and pushing to
           GitHub.
Enumerating objects: 63, done.
Counting objects: 100% (63/63), done.
Delta compression using up to 11 threads
Compressing objects: 100% (60/60), done.
Writing objects: 100% (63/63), 578.91 KiB | 7.93 MiB/s, done.
Total 63 (delta 7), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (7/7), done.
remote: 
remote: Create a pull request for 'gh-pages' on GitHub by visiting:
remote:      https://github.com/kkh451/spacewalks/pull/new/gh-pages
remote: 
To https://github.com/kkh451/spacewalks-dev.git
 * [new branch]      gh-pages -> gh-pages
INFO    -  Your documentation should shortly be available at: https://kkh451.github.io/spacewalks/
```

This command will build our documentation with MkDocs, then commit and push the files to the `gh-pages` branch using the GitHub `ghp-import` tool which is installed as a dependency of MkDocs.

For more options, use:

```bash
mkdocs gh-deploy --help
```

Notice that the deploy command did not allow us to preview the site before it was pushed to GitHub; so, it is a good idea to check changes locally with the build commands before deploying.


::::::
:::::::::::::::::::::::::::::::::::::


:::::: challenge

### Spacewalks how-to guide (15 min)

a. Review the Diataxis guidance page on writing a How-to guide.
Identify three features of an effective how-to guide.

b. Following the Diataxis guidelines, add a how-to guide to the `docs/how-to-guides.md` file in your documentation folder to show users how to change the destination filename for the output CSV dataset generated by the Spacewalks software.

::: solution

An effective how-to guide should:

- be goal oriented and focus on action
- avoid teaching or explanation
- use appropriate language, e.g. conditional imperatives
- have an informative title.

An example how-to guide for our project in the file `docs/how-to-guides.md` could like:

```
## How to change the file path of Spacewalk's output dataset

This guide shows you how to set the file path for Spacewalk's output data set to a location of your choice.

By default, the cleaned data set in CSV format, generated by the Spacewalk software, is saved to the `results/` folder within the working directory with file name `eva-data.csv`.

If you would like to modify the name or location of the output dataset, set the second command line argument to your chosen file path. 
For example, if you want to save the output data set to the subfolder `data/clean/` you can invoke the script as:

python3 eva_data_analysis.py eva-data.json data/clean/eva-data-clean.csv

The specified destination folder `data/clean/` must exist before running spacewalks analysis script.
```

Remember to rebuild your documentation after the above change:

```bash
(venv) $ mkdocs build
```
:::

::::::

The Diátaxis framework provides guidance for developing technical documentation for different purposes.
Tutorials differ in purpose and scope to how-to guides, and as a result, differ in content and style.

::::: challenge

### Spacewalks tutorial (10 min)

Let's adapt the how-to guide from the previous challenge into a tutorial that explains
how to change the file path for the output dataset when running the analysis script.

::: solution

Here is what an example tutorial may look like.

```
## Introduction

In this tutorial, we will learn how to change the file path for the output dataset generated by the Spacewalk software.
By the end of this tutorial, you will be able to specify a custom file path for the cleaned dataset.

## Prerequisites

Before you start, ensure you have the following:

- Python installed on your system
- The Spacewalk script (`eva_data_analysis.py`)
- An input dataset (`eva-data.json`)

## Prepare the destination directory

First, let us decide where we want to save the cleaned dataset and make sure the directory exists.

For this tutorial, we will use `data/clean/` as the destination folder.

Let's create the directory if it does not exist - e.g. from the command line do:

mkdir -p data/clean

```
#### Run the analysis script with a custom path

Next, execute the Spacewalk script and specify the custom file path for the output dataset:
```bash
(venv_spacewalks) $ python3 eva_data_analysis.py <input-file> <output-file>
```

Replace <input-file> with your input dataset (`data/eva-data.json`) and <output-file> with your desired output path
(`data/clean/eva-data-clean.csv`).

Here is the complete command:
```bash
(venv_spacewalks) $ python3 eva_data_analysis.py data/eva-data.json data/clean/eva-data-clean.csv
```

Notice how the output to the command line clearly indicates that we are using a custom output file path.

```output
Using custom input and output filenames
Reading JSON file data/eva-data.json
Saving to CSV file data/clean/eva-data-clean.csv
Adding crew size variable (crew_size) to dataset
Saving to CSV file data/clean/eva-data-clean.csv
Plotting cumulative spacewalk duration and saving to results/cumulative_eva_graph.png
```

After running the script, let us check the `data/clean` directory to ensure the
cleaned dataset has been saved correctly.

```bash
(venv_spacewalks) $ ls data/clean
```
You should see `eva-data-clean.csv` file listed in the `data/clean` folder.

#### Exercise: custom output path

- Create a new directory named `output/data` in your working directory.
- Run the Spacewalk script to save the cleaned dataset in the newly created `output/data` directory with the filename `cleaned-eva-data.csv`.
- Verify that the dataset has been saved correctly.

##### Solution

```bash
# Create the directory:
(venv_spacewalks) $ mkdir -p output/data

# Run the script:
(venv_spacewalks) $ python3 eva_data_analysis.py data/eva-data.json output/data/cleaned-eva-data.csv

# Verify the output:
(venv_spacewalks) $ ls output/data

# You should see cleaned-eva-data.csv listed
```

Congratulations! You have successfully changed the file path for Spacewalks output dataset
and completed an exercise to practice the process. You can now customize the output location
and filename according to your needs.

:::
::::::

Do not forget to commit any uncommitted changes you may have and then push your work to GitHub.

```bash
(venv_spacewalks) $ git add <your_changed_files>
(venv_spacewalks) $ git commit -m "Your commit message"
(venv_spacewalks) $ git push origin main
```

## Summary

In this episode we have highlighted the importance of software project documentation (e.g. README, license, and citation files) in making research code understandable, reusable, and reproducible.

We have also explored tools and formats for delivering tutorials, how-to guides, and reference materials -
like Markdown files, Wikis, and static site generators (e.g. MkDocs) - and highlighted the Diátaxis framework for
structuring documentation effectively.




::: keypoints

- TODO

:::