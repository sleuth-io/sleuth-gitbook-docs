---
description: Automatic tagging for quick deploy history searching
---

# Tags

As you might already know, GitHub tags point to an invidual commit. They're similar to references, but the commit it points to never changes. They're helpful if you want to, say, point to specific release, which is at a specific point in time. 

Sleuth implements tags in a slightly different way. 

{% hint style="info" %}
Sleuth tags are not related to GitHub tags. They are completely different implentations. 
{% endhint %}

If tags are not explicitly defined for a deployment, Sleuth detects tags by matching files using patterns either from a _.sleuth/TAGS_ file in your repository, or a set of default patterns:

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

You can search for tags using the search bar in the Sleuth Dashboard. 

{% hint style="warning" %}
Do **not** use the leading hash \(\#\) when searching for a tag. 
{% endhint %}

![](.gitbook/assets/tags-searching.png)

