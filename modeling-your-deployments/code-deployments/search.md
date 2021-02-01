# Search

Search your entire deployment history using Sleuth's built-in search function. The search field features  search-as-you-type functionality; simply start typing and the previous [deploys](../deploy-cards.md) that contain the entered search terms are displayed. 

![](../../.gitbook/assets/sleuth-sleuth-2021-01-31-15-15-49.png)

You can also filter the deploy cards based on the health of the deploy. For example, you might only want to search deploys that were deemed _Unhealthy_. The dropdown value can be set either before or after you begin searching. 

![](../../.gitbook/assets/sleuth-sleuth-2021-01-31-15-17-19.png)

#### Sleuth searches through all content contained in a deploy:

* Pull request key, summary and descriptions
* Commit hashes and descriptions
* Issue keys, summaries and descriptions
* File names
* Authors username and full name
* Sleuth [tags](tags.md)

#### Use Sleuth search to quickly discover when an issue was deployed:

![](../../.gitbook/assets/sleuth-search-sleuth-2021-01-31-15-24-58.png)

#### Search to find if a pull request was deployed:

![](../../.gitbook/assets/sleuth-search-sleuth-2021-01-31-15-26-43.png)

#### Search to find all the deploys made by one of your developers:

![](../../.gitbook/assets/sleuth-search-sleuth-2021-01-31-15-27-37.png)

### Searching with Slack

If your organization has a Slack integration, you can search directly from the Slack app. You can search from any channel in the integrated organization. 

To search using Slack, type `/sleuth` then your search term. For example:

```text
/sleuth memory leak 
```

Search results are displayed in the same channel. The most recent 5 changes are returned. You can click the View all button to view all search results in Sleuth.

![](https://img.announcekit.app/c7ffa9371e0cceec595ff6dd4e532fc4?s=7190d548eec84959d4d185c1b435b101)

By default `/sleuth MY SEARCH TEXT` will search all projects in the organization with the Slack integration for matching deploys.

