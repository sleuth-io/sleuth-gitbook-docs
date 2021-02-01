---
description: Automatic tagging for quickly searching through your deploy history
---

# Automatic tags

Sleuth allows you to setup rules to automatically tag your deploys. Tagging deploys allows you to flag deploys that may require a different level of attention, such as a database migration. Tags are also a quick way to organize and quickly search similar deploys.

The tags are added by looking for patterns in the files deployed in your code repositories. For example, if Sleuth finds a **pom.xml** file in your deploy, it automatically adds the tag **\#dependencies** to the deploy. 

Tags are searchable via everywhere [search](search.md) is exposed. See the table below for more patterns and tags Sleuth automatically applies to your deploys based on pattern matching. 

![ The \`migration\` tag was automatically added to the deploy](../../.gitbook/assets/sleuth-sleuth-2021-01-31-14-01-42.png)

If tags are not explicitly defined for a deployment, Sleuth detects tags by matching files using patterns either from the _**.sleuth/TAGS**_  file in your repository, or a set of default patterns:

| Pattern | Tag |
| :--- | :--- |
| \*\*/migration/\*\* | \#migration |
| Pipfile.lock | \#dependencies |
| requirements.txt | \#dependencies |
| package-lock.json | \#dependencies |
| pom.xml | \#dependencies |
| Dockerfile | \#docker |
| \*\*/db/\*\* | \#database |
| \*tf | \#terraform |

### Adding custom tags

In addition to having Sleuth automatically detect patterns and add tags to your deploys, you can add your own patterns that Sleuth can then use to help you search for your previous deploys. This is easily done by editing the _**.sleuth/TAGS**_ in your code repository. 

#### To add your own pattern/tag pair: 

1. Create a _**.sleuth/**_ directory in the root directory of your repo. This repo must be connected as a [code deployment](../../settings/project/code-deployments.md) in Sleuth. 
2. Create a file **TAGS** in the _**.sleuth**_ directory. 
3. Create a matching pattern/tag pair; create additional pairs on new lines.  For example: `/db #database`
4. Save the file. 

In the example above, a directory with the name `db` would generate a tag `database` in the Sleuth deploy card, which you can then search for quickly using the Sleuth search. 

