Version-Controlled Project with Git

This guide will walk you through setting up and managing a project using Git and GitHub, incorporating best practices for version control. The commands provided are compatible with Windows, macOS, and Linux environments when using a Git-compatible terminal (like Git Bash, PowerShell, or Command Prompt on Windows).



Objective

To effectively manage a project using Git best practices, ensuring proper version control, collaboration, and release management.



Tools

Git



GitHub



Deliverables

A project repository on GitHub.



Proper commit history.



Well-defined branching strategy (main, dev, feature).



Demonstration of pull request usage.



A comprehensive README.md file.



Proper use of .gitignore and Git tags.



Markdown documentation for all tasks.



Step-by-Step Guide

1\. Initialize Repository and Push to GitHub

First, you'll create a local Git repository and then push it to a new repository on GitHub.



a. Create a Local Directory and Initialize Git:



Open your preferred terminal (Git Bash, PowerShell, or Command Prompt) and run:



mkdir my-project

cd my-project

git init



b. Create an Initial File (e.g., README.md and main.py):



On Windows, you can use echo in Command Prompt or PowerShell, or touch and a text editor. For simplicity and cross-compatibility, the echo command shown below works well in Git Bash, PowerShell, and Command Prompt.



echo "# My DevOps Project" > README.md

echo "This repository manages a DevOps project." >> README.md

echo "print('Hello, DevOps!')" > main.py



c. Add and Commit Initial Files:



git add README.md main.py

git commit -m "Initial commit: Add README and basic main script"



d. Create a Repository on GitHub:



Go to GitHub.



Click the + sign in the top right corner and select New repository.



Give it a name (e.g., my-devops-project).



Choose Public or Private.



Do NOT initialize with a README, .gitignore, or license (we're doing that locally).



Click Create repository.



e. Link Local Repository to GitHub and Push:



After creating the GitHub repository, you'll see instructions to link your existing local repository. Use these commands:



git remote add origin https://github.com/YOUR\_GITHUB\_USERNAME/my-devops-project.git

git branch -M main

git push -u origin main



Replace YOUR\_GITHUB\_USERNAME with your actual GitHub username.



2\. Create dev and feature Branches

Adopt a branching strategy where main is for production-ready code, dev is for ongoing development, and feature branches are for new features or bug fixes.



a. Create the dev Branch from main:



git checkout -b dev

git push -u origin dev



b. Create a feature Branch from dev:



For each new feature or significant change, create a dedicated feature branch.



git checkout -b feature/add-new-functionality dev



3\. Use Pull Requests to Merge Changes

Pull requests (PRs) are crucial for code review and merging changes safely.



a. Make Changes in the feature Branch:



Let's simulate adding a new function. The echo command with >> appends content to the file.



\# Edit main.py

echo "

def new\_function():

&nbsp;   return 'New functionality added!'



print(new\_function())

" >> main.py



b. Add and Commit Changes to the feature Branch:



git add main.py

git commit -m "feat: Add new\_function to main.py"



c. Push the feature Branch to GitHub:



git push -u origin feature/add-new-functionality



d. Create a Pull Request on GitHub:



Go to your GitHub repository.



You'll see a prompt to create a Pull Request from feature/add-new-functionality to dev. Click Compare \& pull request.



Add a descriptive title and description for your PR.



Assign reviewers (optional).



Click Create pull request.



e. Review and Merge the Pull Request:



Review: Someone (or you, for this exercise) would review the code changes.



Merge: Once approved, click Merge pull request and then Confirm merge.



Delete Branch (Optional but Recommended): After merging, GitHub offers to delete the feature branch. It's good practice to delete merged branches to keep the repository clean.



f. Pull dev Changes Locally:



After merging on GitHub, update your local dev branch.



git checkout dev

git pull origin dev



g. Merging dev to main (for releases):



When dev is stable and ready for a release, you would create a PR from dev to main.



git checkout main

git pull origin main # Ensure main is up-to-date

git merge dev # Merge dev into main locally (or create a PR on GitHub)

git push origin main # Push the merged main to GitHub



For a real project, you would create a PR on GitHub from dev to main for final review and approval before deploying to production.



4\. Add a Proper README.md

A good README.md is essential for project understanding.



a. Enhance README.md:



\# My DevOps Project



This repository serves as a practical example for managing a DevOps project using Git best practices.



\## Table of Contents

\- \[Project Overview](#project-overview)

\- \[Getting Started](#getting-started)

\- \[Branching Strategy](#branching-strategy)

\- \[Contributing](#contributing)

\- \[License](#license)



\## Project Overview

This project demonstrates:

\- Git repository initialization and GitHub integration.

\- Implementation of `main`, `dev`, and `feature` branches.

\- Workflow for Pull Requests (PRs) for code review and merging.

\- Usage of `.gitignore` to exclude unnecessary files.

\- Application of Git tags for release management.



\## Getting Started



\### Prerequisites

\- Git installed on your local machine. You can download it from \[git-scm.com](https://git-scm.com/download/win).

\- A GitHub account.



\### Installation

1\. Clone the repository:

&nbsp;  ```bash

&nbsp;  git clone \[https://github.com/YOUR\_GITHUB\_USERNAME/my-devops-project.git](https://github.com/YOUR\_GITHUB\_USERNAME/my-devops-project.git)

&nbsp;  cd my-devops-project



Running the Project

python main.py



Branching Strategy

We follow a simplified Gitflow-like model:



main: Production-ready code. Only stable, tested releases are merged here.



dev: Integration branch for ongoing development. All new features are merged here first.



feature/<feature-name>: Branches for developing new features or bug fixes. They branch off dev and merge back into dev via Pull Requests.



Contributing

Fork the repository.



Create your feature branch (git checkout -b feature/AmazingFeature dev).



Commit your changes (git commit -m 'feat: Add some AmazingFeature').



Push to the branch (git push origin feature/AmazingFeature).



Open a Pull Request from your feature branch to the dev branch.



License

Distributed under the MIT License. See LICENSE for more information.





\*\*b. Commit and Push the Updated `README.md`:\*\*



```bash

git add README.md

git commit -m "docs: Enhance README with project details and guidelines"

git push origin dev # Push to dev, then create a PR to main if ready for release documentation



You would typically merge this into dev first, then dev to main when ready.



5\. Use .gitignore and Tags

.gitignore prevents unwanted files from being committed. Tags mark significant points in history, like releases.



a. Create a .gitignore File:



This file lists patterns for files Git should ignore (e.g., compiled files, temporary files, environment variables). You can create this file using a text editor or the echo command.



\# Python specific ignores

\_\_pycache\_\_/

\*.pyc

\*.pyo

\*.pyd

.Python

env/

venv/

\*.env

.vscode/



\# Operating System files

.DS\_Store

Thumbs.db



\# Logs and temporary files

\*.log

\*.tmp

\*.temp



Save this content as a file named .gitignore in the root of your project.



b. Add and Commit .gitignore:



git add .gitignore

git commit -m "chore: Add .gitignore file"

git push origin dev



c. Create a Git Tag for a Release:



Once main has a stable version, tag it.



git checkout main

git pull origin main # Ensure your local main is up-to-date

git tag -a v1.0.0 -m "Release version 1.0.0"

git push origin v1.0.0



This creates an annotated tag and pushes it to GitHub.



6\. Document All Tasks Using Markdown

As demonstrated throughout this guide, documenting your workflow, decisions, and tasks using Markdown within your repository (e.g., in README.md, or a docs/ directory) is a best practice.



Example of a docs/ directory structure:



my-devops-project/

├── .git/

├── .gitignore

├── README.md

├── main.py

└── docs/

&nbsp;   ├── architecture.md

&nbsp;   ├── deployment-guide.md

&nbsp;   └── contributing-guidelines.md



Outcome

By following these steps, you will have a well-structured Git repository on GitHub, demonstrating a practical version control workflow for a DevOps project. You'll be familiar with:



Repository initialization and remote linking.



Implementing a robust branching strategy (main, dev, feature).



Utilizing Pull Requests for collaborative code review and merging.



Creating informative README.md files.



Managing ignored files with .gitignore.



Marking significant releases with Git tags.



The importance of documentation in Markdown.

