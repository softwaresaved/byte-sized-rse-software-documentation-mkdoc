---
title: "Introduction"
teaching: 30
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
We also discuss different types of software documentation aimed at various target audiences, including end users, developers, maintainers, administrators and contributors.

## What is software documentation?

Software documentation provides the information needed to understand, use, maintain and reuse software. 
It explains the software's purpose, functionality, installation, configuration and operation - helping users and contributors work with the software effectively.

Documentation also captures important software project information and metadata that support long-term sustainability and reuse. 
This may include details about licensing, project ownership and maintenance, contributor roles, contact information, support channels, issue reporting processes and guidance on how the software should be cited and credited. 
Together, this information helps ensure that software remains accessible, reusable and maintainable throughout its lifecycle.

## Who is documentation for?

Different audiences interact with our software in different ways and therefore require different types of documentation.
Understanding who your documentation is for helps you decide what information to include, how much detail to provide, and the style in which it should be written.

Common audiences for software documentation include:

* **End users** want to use the software to achieve a goal rather than understand how it is implemented. They need documentation that helps them install, learn, and operate the software efficiently.
* **Developers** work on the software's codebase to add features, fix bugs and improve functionality. They need technical information that helps them understand how the software works (covering software architecture, code structure, APIs, testing procedures) and information on development workflows/practices so they can contribute code effectively.
* **Contributors** contribute to the project but may not be part of the core development team. They need guidance on contribution processes, project expectations, coding standards and community practices. 
  Code contributors will also need access to developer documentation.
* **Maintainers** are responsible for the long-term health and sustainability of the software project.
  They need documentation covering releases, governance, maintenance procedures, project management, and decision-making processes, as well as technical developer documentation. 
* **System administrators** deploy, configure, monitor and maintain software in operational environments. 
  They need documentation on installation, configuration, deployment, system requirements, security, monitoring, backup and troubleshooting (but may not need to know all the implementation/code details or design decisions).

You may not have all of these audiences for your software, but you will almost certainly have end users and developers. 
A single document may serve multiple audiences, so information does not necessarily need to be duplicated. 
For example, installation documentation can be useful to end users, developers, contributors, maintainers and system administrators alike.

When planning documentation, identify your primary audiences and ensure that each has access to the information they need to successfully use, contribute to, maintain or operate the software.

## Why does documenting software matter?

Software documentation is often seen as a time-consuming task with few immediate rewards and is therefore frequently neglected in research projects. 
However, documentation is an essential part of software development and research practice. 
Good documentation not only helps others understand and use software, but also improves the quality, sustainability and reproducibility of the research it supports.

Good software documentation:

- captures important methodological details that can be referenced when publishing research findings or preparing reports and papers.
- helps you revisit a project more easily after weeks, months, or even years away from it.
- makes software easier to understand, reuse and build upon, increasing its visibility, adoption, and potential impact.
- supports reproducible research by providing clear information about how the software works and how it should be used.
- facilitates collaboration by helping new team members quickly understand the project and become productive.
- reduces support requests and saves time by answering common questions and providing guidance for users.
- improves software sustainability by making it easier to maintain, update, and transfer knowledge between project members.

In short, documentation is an investment that benefits both current and future users, contributors and maintainers of a software project.

## Types of software documentation

Software documentation can be produced at different levels and for different audiences. 
A useful way to think about documentation is to group it into three broad categories:

- **Code-level documentation** – information embedded within the source code that explains how the code works.
- **Software-level documentation** – documentation that explains how to install, use, configure and contribute to the code.
- **Project-level documentation** – documentation that describes the wider software project, including its governance, maintenance, licensing, support and sustainability.

These categories complement one another and together provide the information needed to develop, use, maintain, and reuse software effectively. 
In the following sections, we will explore each type in more detail.

## Code-level documentation

Common forms of code-level documentation include **comments** and **documentation strings (docstrings)**.

Code comments are free-text explanations of how specific lines of code work (e.g. logic and implementation details) and are ignored by the interpreter or compiler.

Docstrings are built-in literal strings placed immediately after the definition of a function, class, module, or method that follow a certain syntax. 
They explain how to use the code — including its arguments, return values, and usage — so that other developers and automated tools can understand it without reading the implementation. 
Unlike comments, docstrings are retained as part of the running program, and many tools can automatically display docstring information as part of an interactive documentation or help system (as we will see later on in this lesson).

Comments help convey the context, rationale, and implementation logic of the code. 
They can serve as useful reminders about why code was written in a particular way, how it achieves a specific task or the real-world implications of its behaviour.

Target audience for this type of documentation: developers and maintainers of the software, including your future self.

When writing comments, keep the following principles in mind:

* Focus on why the code exists and how it works, rather than simply describing what it does.
* Avoid comments that merely repeat information that is already obvious from the code.
* Prefer clear, readable code over excessive commenting. If a section of code is difficult to understand, consider refactoring it before adding explanatory comments.
* Keep comments concise and focused. Large blocks of text are difficult to read and maintain.
* Update comments whenever the code changes. Outdated or misleading comments can be more harmful than having no comments at all.
* Use comments to record important assumptions, limitations or workarounds that may not be apparent from the code itself.

## Software-level documentation

Comments and docstrings improve the readability and maintainability of source code, but they are not sufficient on their own to make software easy to use, understand, deploy or contribute to. 
This requires additional software-level documentation aimed at different audiences and their specific needs.

Common examples of software-level documentation include:

- **Technical documentation** for developers, maintainers, contributors and system administrators including high-level software architecture descriptions, API documentation, setup and deployment guides, configuration instructions, testing procedures, error codes and troubleshooting information.
- **User documentation** for end users including installation guides, tutorials, user manuals, example workflows, FAQs and troubleshooting guides that help users learn and use the software effectively without requiring direct support from the development team.

A useful framework for organising software documentation is [Diátaxis][diataxis-framework] (shown in the diagram below), which categorises documentation according to the needs of the reader and the purpose the documentation serves. 

![](https://diataxis.fr/_images/diataxis.png)

Diátaxis identifies four complementary types of documentation:

- **Tutorials** - lessons that guide learners through a series of exercises to build proficiency using the code. Target audience: new users and learners who are unfamiliar with the software.
- **How-to guides** - step by step instructions on how to accomplish specific goals using the software. Target audience: existing users who want to complete a particular task.
- **Reference documentation** - lookup material that helps users find precise information about the software, such as functions, commands, parameters, APIs, and configuration options. 
Reference documentation can often be generated automatically from code-level docstrings. Target audience: developers, advanced users, and maintainers who need accurate technical details.
- **Explanations** - conceptual discussions that help users understand implementation decisions, design choices, and underlying principles. 

- Target audience: developers, maintainers, contributors and system administrators who need to understand the reasoning behind the software.

Other documentation frameworks and communities, such as [Write the Docs][write-the-docs] and [The Good Docs Project][the-good-docs-project], provide a wealth of resources to help teams create high-quality documentation.

You do not need to provide every documentation type described above. 
Instead, focus on creating documentation that meets the needs of your intended audiences. 
The exact mix of documentation will depend on your software, its complexity, and the people who use, contribute to, deploy and maintain it.

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


::: keypoints

TODO
:::