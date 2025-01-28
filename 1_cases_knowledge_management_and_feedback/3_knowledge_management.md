# Knowledge Management

The knowledge management solution allows for articles to be created, reviewed
and published. We can manage different versions and translations. We can also
analyse usage to guide further development.

## Creation

There is a rich text editor. This makes it easy to compose articles using images
and videos. We can also add attachments. As with emails, the number of
attachments is not limited, however, the file sizes are capped at 32mb per
attachment by default.

### AI Sugestions for Keywords and Descriptions

We can enable this from the insights section of Admin Center. We can also
configure data mapping here. By default, the fields are:

- Title
- Content

The relevant control will also need to be present in the form.

The model will only use the first 2,200 chars to generate suggestions.

### Timeline

There is a timeline, this can be useful for tracking activities while working
on the article. For instance, a reviewer may attach notes here for the author.

### Templates

We can create templates to help maintain a consistent style and increase
productivity. This is done from Admin Center -> Knowledge -> Article Templates

## Review

To approve an article, the user must have the requisite role. A specific role:

- Knowledge Manager

Is the most specific role to this functionality.

## Publishing

We can publish an article once it has been approved. We can optionally publish
translations at the same time.

This may be immediate or scheduled.

The article, may be internal or public. Internal articles will not be available
in a public portal.

## Feedback

In addition to notes, a reviewer or user may leave feedback for a given article.
We can provide a written feedback and a score.

## Versions and Translations

Dynamics keeps track of article versions. There are major and minor versions.
We can create these from the command bar.

Similarly, we can create translations from the command bar.

In both instances, we get a new version or translation of the article. The
content is inherited and we must change this manually.

## Article Categories

We can manage categories from the Admin Center. We can also define a parent
category for a given category allowing us to set-up a hierarchical structure.

This is useful when searching for articles. It can also be used to organise
articles in a Portal.

## Filters

Filters are also used to help agents find articles. We can set up a range of
filters to be used with the Knowlege Search Controls.

Optionally, we can also enable agents to personalise these filters.

We can also use the preselected option to make the filter preselected by
default.

We can use the visibility option to determine if the filter is visible to
agents.

To enable a custom field as a search filter, we need to add it to the Quick Find
Knowledge Articles View. To do this, open the properties of the view, in the
find by section, add the column to this list.

- Options Sets, Multiselect Options Sets and Two Choices
- Lookup
- Date and time

I really cannot get this working. It may be worth having another look, I have
added subject but it is not coming up as a filter type

## External Search Providers

We can add the following providers:

- Cross-Organisational: Different D365 instance
- SharePoint in the same tenant
- Microsoft Graph Connector

## Integrated Search Providers

This is similar to the above but it is used for 3rd party providers. We need to
provide much more configuration to set-up the connection.

- Auth: Url and sitemap
- Schema: A schema to map fields to a knowledge article record
- Refresh Schedule

## Analytics

In workspace there is a Knowledge Analytics Page. We can enable this from
insights. The tabs include:

- Search Term Analytics
  - Terms searched
  - Terms without results
  - Engagement for searches
  - Etc
- Article Insights
  - Views
  - Avg Feedback
  - Popular Articles
  - Etc

### Author and Manager Dashboards

There are dashboards for article authors and managers to help manage the
workload.

### Per Article Analytics

Each article has an analytics tab we can use to view analytics and feedback for
that article.

## Using Articles

We can search for articles from various places. For instance, the related pane
and the productivity panel. We can also embed knowledge article search controls
in any form we wish.

### Emailing Links

We can allow agents to copy links to an article. For this to work the article
must be hosted in a public portal and this portal must be linked to Customer
Service by providing the url.
