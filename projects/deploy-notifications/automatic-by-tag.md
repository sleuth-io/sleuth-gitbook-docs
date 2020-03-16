# Automatic by tag

With this option selected, Sleuth will add a POST-commit hook to your repository on [Bitbucket](https://bitbucket.org/) or [GitHub](https://github.com/).

This will ping Sleuth every time a commit is made. When Sleuth detects a tag against your project's branch, a new deploy will be registered.

A tag name can be anything, but we suggest something like: 

```text
production_2015-04-18--16-15
```

To tag your code and push changes to your remote repository, use a similar command:

```text
git tag production_2015-04-18--16-15
git push git@github.com:joeuser/myrepo.git production_2015-04-18--16-15
```

