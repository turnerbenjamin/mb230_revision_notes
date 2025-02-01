# Customer Service Insights

This was a stand-alone application, we now use embedded Customer Service 
Insights features within core applications.

Insights uses natural language models to generate insights, e.g.
- Similar case suggestions
- Knowledge article suggestions

## Enabling Customer Service Insights

Insights are disabled by default. These may be enabled from within Admin Center.

We can configure each of these reports separately

## Customer Service Insights Reports

Once enabled in Customer Service, Insights provides various reports and 
dashboards:
- Customer Service Historical Analytics
- Knowledge Search Analytics
- Smart Assist
- Analytics in Power BI

### Customer Service Historical Analysis

To view this report, users will need a security role with read privileges to the
Customer Service Historical Analytics table.

This shows contains:

- Summary: Overview of customer service KPIs for queues, channels and agents
- Agent: Charts and KPIs for agents and overall agent performance
- Topics: Breakdown of cases and assigned topics


#### Topic Clustering

Topic clustering is dependint on the Historical Analytics report. So this must
be enabled first.

By default, the case title is used for topic clustering. We can change this to
any other column on the case table.

We can specify phrases that we want to be disregarded in the data cleaning 
section. This can help to remove extraneous information like product name,
case status or tags.

Topics identified may be used with Copilot Studio chatpbots. We can make the
topics available to chyat bots by enabling Power Virtual Agents.

### Knowledge Search Analytics

Again, the users will need to have read privileges on the table and this report
needs to have been enabled.

This shows various metrics related to knowlege search. It has sections on:

- Search terms
- Article usage