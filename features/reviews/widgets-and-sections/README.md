# Widgets and Sections

#### Adding Widgets

*   To add a Widget to a Review, drag it from the **Insert** menu on the right-hand side of the Review. Available "drop zones" in the review will highlight when you drag the Widget over them.&#x20;

    <figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
* Hover over any Widget to view its description.
* Search for Widgets by typing into the search field in the **Insert** menu. Only Widgets with matching titles or descriptions will be displayed. \
  ![](<../../../.gitbook/assets/CleanShot 2024-11-06 at 16.03.47.png>)

#### Removing Widgets

To remove a Widget from a Review, expand the [Widget settings](./#widget-settings) ellipsis and select **Delete**. The widget remains available for selection in the **Insert** pane.

#### Resizing and arranging Widgets

* Widgets display in full width by default, but you can reduce them to half width by selecting **Half with** in the Widget's settings menu (see prior screen shot). This allows you to display two Widgets in a single row.
* You can also drag Widgets above or below one another within a Section, and you can drag any half-width Widget to either side of another half-width Widget. It's not possible to drag a Widget from one Section to another.

{% hint style="info" %}
It's not possible to add, remove, or arrange Widgets when a Review is in the **Published** state. See [Review states](https://help.pulse.sleuth.io/features/reviews/review-workflow#review-states) for more information.
{% endhint %}

## Widget settings

Click the ellipsis in the upper-right corner or any Widget to expand its **Widget settings** menu.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-11-05 at 15.47.15@2x.png" alt=""><figcaption></figcaption></figure>

The options presented in the **Widget settings** menu vary depending on the Widget type. Common ones include:

* **Half width** / **Full width:** Toggle the size of the widget between full-width and half-width. See [Resizing and Arranging Widgets](./#resizing-and-arranging-widgets).
* **Configure:** Displays a pop-up modal with configuration settings specific to the Widget (title, display options, filters, etc.). Available configuration settings vary by Widget type. See [Configuring Widgets](./#configuring-widgets) for more information.
* **Scope data:** Available only for Widgets that display data sourced automatically from integrations, this item displays a pop-up modal that allows you to scope the data included in the widget to contributing users and teams (i.e. PR authors/reviewers and issues assignees). See[ Scoping Widget Data ](./#scoping-widget-data)for more.
* **Download xlsx:** Widgets that display data sourced automatically from integrations include this option to download a spreadsheet containing the detailed data behind the chart. This is useful for drilling deeper into outliers and also for confirming any [filter](./#configuring-widgets) or [scoping](./#scoping-widget-data) options you've selected in Widget Settings &#x20;
* **Delete:** Removes the widget from the Review. The Widget can always be added back to the Review by dragging it back in from the Widget Menu

### Configuring Widgets

Access a Widget's configuration options by clicking **Configure** in the **Widget Settings** menu. Available configuration options differ depending on Widget type.&#x20;

* **Automated data Widgets:** For Widgets that display data automatically-sourced data common configuration options include **Value type**, **Display format**, **Calculation**, and **Filters:**

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

*   **Manual data Widgets:** For Widgets that require manual data manually, this screen presents the UI for users to enter that data.\
    &#x20;&#x20;

    <figure><img src="../../../.gitbook/assets/CleanShot 2024-11-06 at 09.51.09@2x.png" alt=""><figcaption></figcaption></figure>

### Scoping Widgets by contributing Users & Teams

Automated data Widgets might display a **Scope data** option that allows you to filter the data in the Widget by contributing users and teams (i.e. named  issue assignees or PR authors/reviews). &#x20;

Scoping options specified here will override scoping options set on the [Teamspace](broken-reference).

<figure><img src="../../../.gitbook/assets/CleanShot 2024-11-06 at 10.00.26@2x.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The **Scope data** screen is specifically for filtering by named contributors. Additional Widget filter options (e.g. by Repository, Issue Type, etc.) are available in the Widget's [**Configure**](./#configuring-widgets) screen.&#x20;
{% endhint %}
