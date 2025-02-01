# Deploy Contact Center

## Set-Up Omni-Channel

We can add Omnichannel for Customer Service to our enviroment using 
admin.powerplatform. 

When we install this, we can step through the various channels and set-them up.
If we do not set-up capabilities for a channel then we cannot go back and do
this later. The channels available are:
- chat
- voice
- sms
- social
- Microsoft Teams

## Set-Up AI Features for Agents

### Sentiment Analysis

This can be enabled from the insights tab of the Admin Center. This should be
enabled by default.

Sentiment analysis is based on the last 6 messages received from the customer 

#### Agent Settings

For active sessions, sentiment analysis will be displayed in the communication
panel. For inactive sessions, we can set sentiment alerts to notify agents if
sentiment falls below a particular value. This is enabled from Insights.

#### Supervisor Settings

For supervisors, there is an Ongoing Conversations dashboard which can show 
sentiment analysis for onging conversations.

We can also send supervisors notifications when sentiment falls below a specific
value. This is configured from insights as well. The supervisor must be assigned
to the given queue to receive sentiment notfications for items in that queue.

### AI Contact Suggestions

This can be enabled from Admin Center -> Collaboration -> Embedded Chat Using
Teams.

For a given record, e.g. case, we can configure the settings to enable AI based
contact suggestions.

This will suggest constacts based on:

- The number of similar cases the contacts have resolved
- Similarity level relative to the active case
- How recently the suggested contacts resolved similar cases
- Average time suggested contacts took to resolve the similar cases

It looks like this feature requires that AI suggestions for similar cases has
also been enabled.

### Summaries

We can enable case and conversation summaries from Admin Center -> Productivity
-> Summaries. 

We can also enable CoPilot features such as:
- Allowing agents to ask questions
- Allowing copilot to suggest a response in customer chat
- AI assistenace to draft emails

### Insights Dashboards

The omni channel insights dashboard is split into two sections:

- The insights dashboard: Contains information about KPIs
- Sentiment Analysis: Overview of KPIs and trends related to sentiment analysis

#### Set-Up

- Download the Omnichannel Insights for 365 app and configure it to display
channels and sentiment analysis dashboards
- To configure dashboards we need admin privileges for Customer Service and
Power BI. We also need a Power BI Pro licence 
- We also need to enable embedding of Power BI reports in 365 Customer Service 
in the admin center

To add the insights dashboard, once created, select new dashboard and select Power BI
Dashboard. Set the workspace and Dashboard fields to Omnichannel Insights for
D365.

To add the sentiment analysis dashboard the workspace will be Omnichannel 
insights and the dashboard Omnichannel sentiment analysis

#### Customisation

Custom fields will not show automatically within the Power BI model. We would 
need to edit and extend the report to include these fields.
