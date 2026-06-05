---
title: "Introduction"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- Why are documentation and software (repository) metadata important?
- How should we document our code?
- What are the minimum elements of software documentation needed?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe the main types of software documentation and their target audiences.

::::::::::::::::::::::::::::::::::::::::::::::::

This session introduces the importance of documenting our software. 
We also discuss different types of software documentation and metadata aimed at various target audiences - developers, maintainers, administrators and end users of our software.

## What is software documentation?

The purpose of software documentation is to communicate important information about our software (its purpose, dependencies, how to install and run it, etc.) to the people who use it.
It also includes other additional important information and metadata about our software project that are tangential to the usage instructions.
For example, is it licenced for reuse, who are the developers and maintainers of the project, who to contact about the project, where to report issues or find help, how to cite and credit the software.

## Why does documenting software matter?

Software documentation is often perceived as a thankless and time-consuming task with few tangible benefits and is often neglected in research projects. 
However, documenting our software helps us improve the software and conduct (more) reproducible research.
This is because good software documentation:

- captures important methodological details ready for when we come to publish our research
- helps us return to a project seamlessly after time away
- makes our software more understandable and reusable by others, which can bring us citations and credit
- facilitates collaboration by helping us onboard new project members quickly
- saves us time by answering frequently asked questions (FAQs) about our code for us.

## Know your target audience

Tailoring documentation to the audience’s level of technical understanding ensures it’s relevant and accessible. 
For example, end-users often benefit from simplified explanations and step-by-step instructions, while developers might need technical specs and code samples.

- Comprehensive user documentation allows users to solve common problems, learn new features, and maximize the software’s value without direct support.
1. Know your target audience

## Types of software documentation

Typically we differentiate between:

- code-level documentation
- software-level documentation
- project-level documentation

## Code-level documentation

There are different forms of code-level documentation, including **comments** and **documentation strings (docstrings)**. 

**Code comments** are free-text explanations of how specific lines of code work (e.g. logic and implementation details) and are ignored by the interpreter/compiler.

**Docstrings** are built-in literal strings placed immediately after the definition of a function, class, module, or method. 
They explain how to use the code - including its arguments, returns, usage - so other developers and automated tools can understand its usage without reading the implementation.
Unlike comments, docstrings are retained as part of the running program and there are tools that display docstring information as part of an interactive documentation/help system for your code (as we will see later on).

Commenting is a very useful practice to help convey the context, logic and usage of the code. 
It can be helpful as a reminder for your future self or your collaborators as to why code is written in a certain way, how it is achieving a specific task, or the real-world implications of your code.

Here are a few things to keep in mind when commenting your code:

- Focus on the why and the how of your code - avoid using comments to explain what your code does. If your code is too complex for other programmers to understand, consider rewriting it for clarity rather than adding comments to explain it.
- Make sure you are not reiterating something that your code already conveys on its own. Comments should not echo your code.
- Keep comments short and concise. Large blocks of text quickly become unreadable and difficult to maintain.
- Comments that contradict the code are worse than no comments. Always make a priority of keeping comments up-to-date when code changes.

## Software-level documentation

Comments and documentation strings are an excellent way to improve the documentation and readability of our code, but by themselves are insufficient to ensure that our code is easy to use, understand and modify.
This requires additional technical documentation content and style of which should match its intended purpose and audience.

[Diátaxis framework][diataxis-framework] (shown in diagram below) provides a systematic approach to technical documentation authoring.
It prescribes approaches to content and form that emerge from a systematic approach to understanding the needs of documentation users.

![](https://diataxis.fr/_images/diataxis.png)

According to Diátaxis, technical documentation types (based on their purpose and style) are classified into:

- Tutorials - lessons that guide learners through a series of exercises to build proficiency using the code 
- How-to guides - step by step instructions on how to accomplish specific goals using the code
- References - lookup manuals to help users find relevant information about the software, e.g. functions and their parameters - which can be generated automatically from code-level docstrings
- Explanations - conceptual discussions of the code to help users understand implementation decisions.

Other guides on writing documentation, such as [Write the Docs][write-the-docs] and [The Good Docs Project][the-good-docs-project] provide a range of resources including documentation templates to help us write quality documentation.

You do not have to have all of the above documentation types but you should aim to have at least some documentation for each of your intended audiences:

- Technical documentation for developers and administrators - including the information necessary to develop, deploy, and maintain software. 
For example, high-level architecture and low-level processes such as configurations, error codes, troubleshooting steps, and setup guides; API documentation; testing documentation.
- User documentation for end-users including installation guides, user manuals, and step-by-step instructions and example usages to help users understand, learn new feature sand use the software effectively; FAQs and troubleshooting guides to solve common problems without direct support.

## Project-level documentation

Project-level documentation includes various information and metadata about software that help to discover it, explain the legal terms of reusing it, describe its functionality and purpose on a high level and provide pointers to other types of documentation for your software.

A common way to provide project-level documentation is to include various metadata files in the software repository together with code.
Some common examples of repository metadata files and their role are explained in the table below.

| File            | Description                                                                                                                                                                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| README          | Provides an overview of the project. It can either include inline information or pointers to separate installation instructions and dependencies, usage instructions for running the code or example use cases, links to other metadata files (LICENSE, CITATION, CONTRIBUTING, AUTHORS, etc.) and technical documentation (tutorials / how-tos / references) |
| CONTRIBUTING    | Explains to developers how to contribute code to the project including processes and standards that should be followed                                                                                                                                                                                                                                        |
| CODE_OF_CONDUCT | Defines expected standards of conduct when engaging in a software project                                                                                                                                                                                                                                                                                     |
| LICENSE         | Defines the (legal) terms of using, modifying and distributing the software                                                                                                                                                                                                                                                                                   |
| CITATION        | Provides instructions on how to cite the software                                                                                                                                                                                                                                                                                                             |
| AUTHORS         | Provides information on who authored the software (can also be included in CITATION.cff in which case this file is not needed)                                                                                                                                                                                                                                |


Many of these files can be described as "social documentation", i.e. they indicate how users should “behave” in relation to or "interact" with our software project.
Additional documentation may include:

- Developer onboarding - helps new team members quickly get up to speed with a project, including key development practices and tools in use to establishes a standardised knowledge foundation across team members.
- Contributor guide - similar to developer onboarding but includes a wide range of external contributors for open projects (and not just technical contributors/internal team members working on software development)
- Release notes - summaries for users detailing new features, updates, fixes, and known issues in the latest software release.


::: callout
## Just enough documentation

For many small projects the following three pieces of project-level documentation may be sufficient: README, LICENSE and CITATION.
:::

Let’s look at each of these files in turn.

### README file
A README file acts as a “landing page” for your code repository on GitHub and should provide sufficient information for users to and developers to get started using your code.

To support the [FAIR principles (Findability, Accessibility, Interoperability, and Reusability)][fair-principles-research-software], certain sections in a README file are more important than others.
Below is a breakdown of the sections that are *essential* or *optional* in a README to align with these principles.

Essential:

- **Purpose of the code** - clearly explains what the code does; essential for findability and reusability.
- **Installation instructions** - step-by-step instructions on how to install the software, ensuring accessibility (either in-line instructions or a pointer to a separate installation guide). 
This may include **dependencies** - an overview of external libraries and tools required to run the code, essential for reproducibility and interoperability.
- **Usage examples** - examples of how to run and use the code, helping users understand its functionality and enhancing reusability.
- **License** - specifies the terms under which the code can be used, which is crucial for legal clarity and reusability (typically a pointer to LICENSE file).
- **Software citation** - provides citation information for academic use, ensuring proper attribution and reusability (typically a pointer to CITATION file).

Optional:

- **Audience (who the code is intended for)** - helps users identify if the code is relevant to them, improving findability and usability.
- **How to get help** - informs users where they can get help, ensuring better accessibility.
- **Contribution guide** - encourages and guides contributions from the community, enhancing the code's development and maintainability.
- **FAQs** - provide answers to common questions, aiding in troubleshooting and improving accessibility.
- **Code of Conduct** - sets expectations for behaviour in the community, fostering a welcoming environment and enhancing accessibility.

### LICENSE file

Copyright allows a creator of work (such as written text, photographs, films, music, software code) to state that they own the work they have created.
Copyright is automatically implied - even if the creator does not explicitly assert it, copyright of the work exists from the moment of creation.
A licence is a legal document which sets down the terms under which the creator is releasing what they have created for others to use, modify, extend or exploit.

Because any creative work is copyrighted the moment it is created, even without any kind of licence agreement, it is important to state the terms under which software can be reused.
The lack of a licence for your software implies that no one can reuse the software at all - hence it is imperative you declare it.
A common way to declare your copyright of a piece of software and the license you are distributing it under is to include a file called LICENSE in the root directory of your code repository.

Here are some tools to help you choose a licence:

- [The open source guide][opensource-licence-guide] on applying, changing and editing licenses.
- [choosealicense.com][choosealicense] online tool has some great resources to help you choose a license that is appropriate for your needs, and can even automate adding the LICENSE file to your GitHub code repository.

### CITATION file

We should add a citation file to our repository to provide instructions on how to cite our code.
A citation file can be a plain text (CITATION.txt) or a Markdown file (CITATION.md), but there are certain benefits to using use a special file format called the [Citation File Format (CFF)][cff].
This format provides a way to include richer metadata about code (or datasets) we want to cite, making it easy for both humans and machines to use this information.

#### Why use CFF?

For developers, using a CFF file can help to automate the process of publishing new releases on [Zenodo][zenodo] via GitHub.
GitHub also "understands" CFF, and will display citation information prominently on the landing page of a repository that contains citation info in CFF.

For users, having a CFF file makes it easy to cite the software or dataset with formatted citation information available for copy+paste and direct import from GitHub into reference managers like Zotero.

#### CFF file format

A CFF file is using the [YAML](https://yaml.org/) key-value pair format.
At a minimum a CFF file must contain the title of the software/data, the type of asset (software or data) and at least one author:

```yaml
# This CITATION.cff file was generated with cffinit.
# Visit https://bit.ly/cffinit to generate yours today!
cff-version: 1.2.0
title: My Software
message: >-
  If you use this software, please cite it using the
  metadata from this file.
type: software
authors:
  - given-names: Anne
    family-names: Researcher
```

Additional and optional metadata includes an abstract, repository URL and more.

#### Creating CFF file and making your software citable

We can create (and later update) a CFF file for our software using an online application called [`cffinit`][cffinit-webapp].

#### Citing

To cite our software (or dataset), once a CFF file has been pushed to our remote repository, GitHub's "Cite this repository" button can be used to generate a citation in various formats (APA, BibTeX).


---
How-to guides and tutorials ensure that users can install our software independently and make use of its basic features.
Reference guides and background information can help developers understand our code sufficiently to modify/extend/repurpose it.
