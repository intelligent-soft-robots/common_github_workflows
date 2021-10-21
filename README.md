GitHub Workflows of the Intelligent Soft Robots Group
=====================================================


This repository contains a collection of generic GitHub workflows (like for
running style checkers and other linters on pull requests) that are used on many
repositories.  They are distributed to the repositories with
[gwm](https://github.com/intelligent-soft-robots/github_workflow_manager).


Update Repositories
-------------------


Requirements:
- [gwm](https://github.com/intelligent-soft-robots/github_workflow_manager)
- [treep](https://pypi.org/project/treep/)


To update the workflows of a set of repositories all these repositories (and
nothing else) need to be present within one directory.  This can easily be
achieved by cloning the `WORKFLOW_REPOS` project with treep:

    $ treep --clone WORKFLOW_REPOS


Now run `gwm` to update the workflows:

    $ gwm put -w path/to/workflows.toml -t ./workspace/src


To create a branch "update_workflows" on all repos and commit the changes:

    $ treep --create-branch WORKFLOW_REPOS update_workflows
    $ treep --add-and-commit "chore: update workflows"


And if you want to push them all automatically:

    $ treep --push


As a last step, a pull request needs to be opened on each affected repo to merge
the update into the main/master branch.  As the updated workflows already get
executed on these pull requests, it is also a good way to check first if the
update causes any trouble (e.g. adding a new linter could result in the check
always failing due to already existing issues in the current code.
