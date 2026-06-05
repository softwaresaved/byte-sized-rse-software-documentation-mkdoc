---
title: "Introduction"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- Why is documenting software important?
- How should we document our code?
- What are the minimum elements of software documentation needed?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe the main types of software documentation and identify their primary audiences, including end users, developers, maintainers, contributors and system administrators.

::::::::::::::::::::::::::::::::::::::::::::::::

This session introduces the importance of documenting our software. 
We also discuss different types of software documentation and metadata aimed at various target audiences, including end users, developers, maintainers, administrators and contributors.

## What is software documentation?

The purpose of software documentation is to communicate important information about our software (its purpose, dependencies, how to install and run it, etc.) to the people who use it. 
It also includes additional information and metadata about our software project that are important for its reuse and maintenance. 
For example: is it licensed for reuse, who are the developers and maintainers of the project, who should be contacted about the project, where issues can be reported or help requested, and how the software should be cited and credited.

## Why does documenting software matter?

Software documentation is often perceived as a thankless and time-consuming task with few tangible benefits and is therefore frequently neglected in research projects. 
However, documenting our software helps us improve the software itself and conduct more reproducible research. 
Good software documentation:

- captures important methodological details ready for when we come to publish our research
- helps us return to a project more easily after time away
- makes our software more understandable and reusable by others, increasing its visibility, reuse, and citation
- facilitates collaboration by helping us onboard new project members quickly
- saves us time by answering frequently asked questions (FAQs) about our code

## Target audiences

Different audiences interact with software in different ways and therefore require different types of documentation. 
Understanding who your documentation is for helps you decide what information to include, how much detail to provide, and the style in which it should be written.

* **End users** want to use the software to achieve a goal rather than understand how it is implemented. They need documentation that helps them install, learn, and operate the software efficiently.
* **Developers** work on the software codebase, adding features, fixing bugs, and improving functionality. They need technical information that helps them understand how the software works and how to contribute code effectively.
* **Contributors** are people who want to contribute to the project but may not be part of the core development team. They need guidance on project processes, expectations, and ways of working. 
If they are contributing code, they need to refer to technical documentation for developers as well.
* **Maintainers** are responsible for the long-term health, quality, and sustainability of the software project. They need documentation that supports software maintenance, releases, governance, and decision-making. 
They would typically also require technical developer documentation in order to contribute bug fixes.
* **System administrators** deploy, configure, monitor, and maintain software in operational environments. Their primary concern is ensuring the software runs reliably and securely but may not need to know all the implementation/code details or design decisions.

A single piece of documentation may serve more than one audience. 
For example, installation guide provides information useful to end users, developers, contributors, maintainers and system administrators. 
When planning documentation, it is helpful to identify your primary audiences and ensure that each has access to the information needed to successfully use, contribute to, maintain, or operate the software.

## Types of software documentation

Typically we differentiate between:

- code-level documentation
- software-level documentation
- project-level documentation

Let's look into each of these types.

## Code-level documentation

Common forms of code-level documentation include **comments** and **documentation strings (docstrings)**.

Code comments are free-text explanations of how specific lines of code work (e.g. logic and implementation details) and are ignored by the interpreter or compiler.

Docstrings are built-in literal strings placed immediately after the definition of a function, class, module, or method. 
They explain how to use the code — including its arguments, return values, and usage — so that other developers and automated tools can understand it without reading the implementation. 
Unlike comments, docstrings are retained as part of the running program, and many tools can automatically display docstring information as part of an interactive documentation or help system.

Comments help convey the context, rationale, and implementation logic of the code. 
They can serve as useful reminders about why code was written in a particular way, how it achieves a specific task, or the real-world implications of its behaviour.

Target audience for this type of documentation: developers and maintainers of the software, including your future self.

Here are a few things to keep in mind when commenting your code:

* Focus on the why and the how of your code rather than what it does. If your code is too complex to understand, consider rewriting it for clarity instead of relying on comments.
* Avoid repeating information that is already obvious from the code itself.
* Keep comments short and concise. Large blocks of text quickly become difficult to read and maintain.
* Comments that contradict the code are worse than no comments at all. Keep comments up to date whenever code changes.

## Software-level documentation

Comments and docstrings are excellent ways to improve the readability and maintainability of code, but by themselves they are insufficient to ensure that software is easy to use, understand, and modify. 
This requires additional software-level documentation whose content and style should match its intended purpose and audience, for example:

- **Technical documentation** for developers and administrators - including the information necessary to develop, deploy, and maintain software.
  For example, high-level architecture and low-level processes such as configurations, error codes, troubleshooting steps, and setup guides; API documentation; testing documentation.
- **User documentation** for end-users including installation guides, user manuals, and step-by-step instructions and example usages to help users understand, learn new features and use the software effectively; 
  FAQs and troubleshooting guides to solve common problems without direct support.

[Diátaxis framework][diataxis-framework] (shown in the diagram below) provides a systematic approach to technical documentation. 
It prescribes documentation types based on the needs of documentation users and the purpose the documentation serves.

![](https://diataxis.fr/_images/diataxis.png)

According to Diátaxis, technical documentation can be classified into four categories:

- Tutorials - lessons that guide learners through a series of exercises to build proficiency using the code. Target audience: new users and learners who are unfamiliar with the software.
- How-to guides - step by step instructions on how to accomplish specific goals using the software. Target audience: existing users who want to complete a particular task.
- Reference documentation - lookup material that helps users find precise information about the software, such as functions, commands, parameters, APIs, and configuration options. 
Reference documentation can often be generated automatically from code-level docstrings. Target audience: developers, advanced users, and maintainers who need accurate technical details.
- Explanations - conceptual discussions that help users understand implementation decisions, design choices, and underlying principles. 
Target audience: developers, maintainers, and contributors who need to understand the reasoning behind the software.

Other guides on writing documentation, such as [Write the Docs][write-the-docs] and [The Good Docs Project][the-good-docs-project], provide a wide range of resources and templates to help teams produce high-quality documentation.

You do not need to provide all of the above documentation types, but you should aim to have documentation that serves each of your intended audiences.

## Project-level documentation

Project-level documentation includes information and metadata that help others discover, understand, evaluate, cite, reuse, and contribute to software.

Target audience: end users, developers, contributors, project managers, funders, and anyone evaluating or reusing the software.

A common way to provide project-level documentation is to include metadata files within the software repository alongside the code. 
Some common examples are shown below.

| File            | Description                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| `README`          | Provides an overview of the project, including links to installation, usage, dependencies, other metadata files and technical documentation. |
| `CONTRIBUTING`    | Contributor onboarding - explains how to contribute to the project, follow project processes and standards, and use common tools.            |
| `CODE_OF_CONDUCT` | Defines expected standards of behaviour within the project community.                                                                        |
| `LICENSE`         | Defines the legal terms under which the software can be used, modified, and distributed.                                                     |
| `CITATION`        | Provides instructions on how to cite the software.                                                                                           |
| `AUTHORS`         | Identifies the authors of the software (often included within a `CITATION.cff` file instead).                                                |
| Release notes | Summaries detailing new features, updates, fixes, and known issues in the latest software release.                                           | 

Many of these files can be considered *social documentation* because they describe how people should interact with a software project and its community.


::: callout
## Just enough documentation

For many small projects the following three pieces of project-level documentation may be sufficient: README, LICENSE and CITATION.
:::

Let’s look at each of these files in turn.

### README file
A README file acts as the landing page for your repository and should provide enough information for users and developers to get started with your software.

To support the [FAIR principles (Findability, Accessibility, Interoperability, and Reusability)][fair-principles-research-software], certain README sections are particularly important.

Essential:

- **Purpose of the software** - clearly explains what the code does; essential for findability and reusability.
- **Installation instructions** - describes how to install and configure the software and its dependencies, essential for reproducibility and interoperability.
- **Usage examples** - examples of how to run and use the code, helping users understand its functionality and enhancing reusability.
- **License information** - links to the LICENSE file and clarifies reuse permissions, crucial for legal clarity and reusability.
- **Citation information** - links to the CITATION file and explains how the software should be cited, ensuring proper attribution and reusability.

Optional:

- **Audience (who the code is intended for)** - helps users identify if the code is relevant to them, improving findability and usability.
- **How to get help** - informs users where they can get help, ensuring better accessibility.
- **Contribution guide** - encourages and guides contributions from the community, enhancing the code's development and maintainability.
- **FAQs** - provide answers to common questions, aiding in troubleshooting and improving accessibility.
- **Code of Conduct** - sets expectations for behaviour in the community, fostering a welcoming environment and enhancing accessibility.

### LICENSE file

Copyright automatically applies to creative works —including software— from the moment they are created. 
A licence is a legal document that specifies the terms under which others may use, modify, redistribute, or build upon that work.

Because software is copyrighted by default, it is important to explicitly state the terms under which it can be reused. 
Without a licence, others generally have no permission to reuse the software.

The standard way to declare licensing terms is to include a file called `LICENSE` in the root directory of the repository.

Useful resources include:

- [The open source guide][opensource-licence-guide] on applying, changing and managing licenses.
- [choosealicense.com][choosealicense] online tool which helps developers select an appropriate licence and generate a LICENSE file.

### CITATION file

A citation file provides instructions on how users should cite your software. 
Citation information can be provided in plain text (`CITATION.txt`) or Markdown (`CITATION.md`), but there are significant benefits to using the Citation File Format (CFF) in `CITATION.cff`.

CFF provides structured, machine-readable metadata that can be understood by repositories, citation services, and reference-management tools.

#### Why use CFF?

For developers, using a CFF file can help to automate the process of publishing new releases on [Zenodo][zenodo] via GitHub. 
GitHub also “understands” CFF, and will display citation information prominently on the landing page of a repository that contains citation info in CFF.

For users, having a `CITATION.cff` file makes it easy to cite the software or dataset with formatted citation information available for copy+paste and direct import from GitHub into reference managers like [Zotero][zotero].

CFF uses the [YAML](https://yaml.org/) key-value pair format.
At a minimum, it must contain:

- the title of the software
- the asset type (e.g. software or dataset)
- at least one author

Example:

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

Additional metadata can include abstracts, repository URLs, version information, identifiers (DOIs), and more.

A CFF file can be created or updated using the online application [`cffinit`][cffinit-webapp].

Once `CITATION.cff` file has been added to a repository, GitHub's "Cite this repository" feature can generate citations in a variety of formats, including APA and BibTeX.

## Summary

Software documentation helps make research software understandable, reusable, maintainable, and citable. 
Different forms of documentation serve different audiences. 
Code-level documentation supports developers and maintainers, user documentation helps people learn and use software, and project-level documentation provides essential information about the software and its community. 
Even small projects benefit from maintaining a README, LICENSE, and CITATION file, which together improve the discoverability, usability, and reusability of software.