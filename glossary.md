# Glossary

### **Magnitude** 💣 

#### Change source

#### **Organizations**

#### **Projects**

Projects contain **change sources**:

#### **Code deployments**

Code deployments track deploys. Deploys collect the code changes, pull requests, issues, and authors deploying to your environment. 

Code deployments also: 

* capture the code reviews in each deploy;
* generate ChatOps notifications of deploys;
* preview what changes a deploy will contain.

#### **Feature flags**

#### **Infrastructure changes**

Projects contain **impact sources:**

* **Error rates**
* **SLIs**
* **Response times**

**Integrations**

**Environments**

* Staging
* Production

## GitHub Glossary

**Blame**

The "blame" feature in Git describes the last modification to each line of a file, which generally displays the revision, author and time. This is helpful, for example, in tracking down when a feature was added, or which commit led to a particular bug.

**Branch**

A branch is a parallel version of a repository. It is contained within the repository, but does not affect the primary or `master` branch allowing you to work freely without disrupting the "live" version. When you've made the changes you want to make, you can merge your branch back into the `master` branch to publish your changes. For more information, see "[About branches](https://help.github.com/en/articles/about-branches)."

**Check**

A check is a type of status check on GitHub. See "[Status checks](https://help.github.com/en/github/getting-started-with-github/github-glossary#status-checks)."

**Clone**

A clone is a copy of a repository that lives on your computer instead of on a website's server somewhere, or the act of making that copy. With your clone you can edit the files in your preferred editor and use Git to keep track of your changes without having to be online. It is, however, connected to the remote version so that changes can be synced between the two. You can push your local changes to the [remote](https://help.github.com/en/github/getting-started-with-github/github-glossary#remote) to keep them synced when you're online.

**Collaborator**

A collaborator is a person with read and write access to a repository who has been [invited to contribute](https://help.github.com/en/articles/how-do-i-add-a-collaborator) by the repository owner.

**Commit**

A commit, or "revision", is an individual change to a file \(or set of files\). It's like when you _save_ a file, except with Git, every time you save it creates a unique ID \(a.k.a. the "SHA" or "hash"\) that allows you to keep record of what changes were made when and by who. Commits usually contain a commit message which is a brief description of what changes were made.

**Contributor**

A contributor is someone who has contributed to a project by having a pull request merged but does not have collaborator access.

**Dashboard**

Your personal dashboard is the main hub of your activity on GitHub. From your personal dashboard, you can keep track of issues and pull requests you're following or working on, navigate to your top repositories and team pages, and learn about recent activity in repositories you're watching or participating in. You can also discover new repositories, which are recommended based on users you're following and repositories you have starred. To only view activity for a specific organization, visit your organization's dashboard. For more information, see "[About your personal dashboard](https://help.github.com/en/articles/about-your-personal-dashboard)" or "[About your organization dashboard](https://help.github.com/en/articles/about-your-organization-dashboard)."

**Diff**

A diff is the _difference_ in changes between two commits, or saved changes. The diff will visually describe what was added or removed from a file since its last commit.

**Enterprise account**

Enterprise accounts allow you to centrally manage policy and billing for multiple GitHub.com organizations. Enterprise accounts are available with GitHub Enterprise Cloud. For more information, see "[About enterprise accounts](https://help.github.com/en/articles/about-enterprise-accounts)."

**Fetch**

Fetching refers to getting the latest changes from an online repository without merging them in. Once these changes are fetched you can compare them to your local branches \(the code residing on your local machine\).

**Fork**

A fork is a personal copy of another user's repository that lives on your account. Forks allow you to freely make changes to a project without affecting the original. Forks remain attached to the original, allowing you to submit a pull request to the original's author to update with your changes. You can also keep your fork up to date by pulling in updates from the original.

**Git**

Git is an open source program for tracking changes in text files, and is the core technology that GitHub, the social and user interface, is built on top of.

**Issue**

Issues are suggested improvements, tasks or questions related to the repository. Issues can be created by anyone \(for public repositories\), and are moderated by repository collaborators. Each issue contains its own discussion forum, can be labeled and assigned to a user.

**Markdown**

Markdown is a simple semantic file format, not too dissimilar from .doc, .rtf and .txt. Markdown makes it easy for even those without a web-publishing background to write prose \(including with links, lists, bullets, etc.\) and have it displayed like a website. GitHub supports Markdown, and you can [learn about the semantics](https://help.github.com/en/categories/writing-on-github).

**Merge**

Merging takes the changes from one branch \(in the same repository or from a fork\), and applies them into another. This often happens as a pull request \(which can be thought of as a request to merge\), or via the command line. A merge can be done automatically via a pull request via the GitHub web interface if there are no conflicting changes, or can always be done via the command line. For more information, see "[Merging a pull request](https://help.github.com/en/articles/merging-a-pull-request)."

**Open source**

Open source software is software that can be [freely used, modified, and shared \(in both modified and unmodified form\) by anyone](http://opensource.org/definition). Today the concept of "open source" is often extended beyond software, to represent a philosophy of collaboration in which working materials are made available online for anyone to fork, modify, discuss, and contribute to.

For more information on open source, specifically how to create and grow an open source project, we've created [Open Source Guides](https://opensource.guide/) that will help you foster a healthy open source community. You can also take a free [GitHub Learning Lab](https://lab.github.com/) course on maintaining open source communities.

**Organization**

Organizations are shared accounts where businesses and open-source projects can collaborate across many projects at once. Owners and administrators can manage member access to the organization's data and projects with sophisticated security and administrative features.

**Private repository**

Private repositories are repositories that can only be viewed or contributed to by their creator and collaborators the creator specified.

**Pull**

Pull refers to when you are fetching _in_ changes _and_ merging them. For instance, if someone has edited the remote file you're both working on, you'll want to _pull_ in those changes to your local copy so that it's up to date.

**Pull request**

Pull requests are proposed changes to a repository submitted by a user and accepted or rejected by a repository's collaborators. Like issues, pull requests each have their own discussion forum. For more information, see "[About pull requests](https://help.github.com/en/articles/about-pull-requests)."

**Push**

Pushing refers to sending your committed changes to a remote repository, such as a repository hosted on GitHub. For instance, if you change something locally, you'd want to then _push_ those changes so that others may access them.

**Remote**

This is the version of something that is hosted on a server, most likely GitHub. It can be connected to local clones so that changes can be synced.

**Repository**

A repository is the most basic element of GitHub. They're easiest to imagine as a project's folder. A repository contains all of the project files \(including documentation\), and stores each file's revision history. Repositories can have multiple collaborators and can be either public or private.

**SSH key**

SSH keys are a way to identify yourself to an online server, using an encrypted message. It's as if your computer has its own unique password to another service. GitHub uses SSH keys to securely transfer information to your computer.

**Status**

A status is a type of status check on GitHub. See "[Status checks](https://help.github.com/en/github/getting-started-with-github/github-glossary#status-checks)."

**Status checks**

Status checks are external processes, such as continuous integration builds, which run for each commit you make in a repository. For more information, see "[About status checks](https://help.github.com/en/articles/about-status-checks)."

**Team**

Teams are groups of organization members that reflect your company or group's structure with cascading access permissions and mentions.

**Upstream**

When talking about a branch or a fork, the primary branch on the original repository is often referred to as the "upstream", since that is the main place that other changes will come in from. The branch/fork you are working on is then called the "downstream".

**User**

Users are personal GitHub accounts. Each user has a personal profile, and can own multiple repositories, public or private. They can create or be invited to join organizations or collaborate on another user's repository.



