# Implement Copilot for Customer Service

## Configure Copilot in Customer Service

We can make Copilot available to Agents in Insights. There are various options
here such as enable for customer chat and email.

Once enabled, we can customise access further using the Copilot AI Features
pane in an Agent Experience Profile

### What can it Do?

Copilot can be used to help agents with tasks such as:

- Responding to questions
- Composing emails
- Drafting chat responses
- Summarising a case and conversation (Workspace only)

### Configure Knowledge Services

We can configure the sources that copilot uses for knowledge. We can select
knowledge base to allow this to be used for the ask a question and draft an
email feature.

We may also add trusted websites as sources. Copilot will look up to 2 levels
down from the domain for information.

### Summaries

We can configure the summaries provided by Copilot in Admin Center ->
Productivity -> Summaries. There are various options we can configre here such
as:

- Fields used for summaries for custom record types
- When live summaries are made available
- Information to exclude from summaries
- Whether to collect agent usage data for analytics
- Managing fields used for case summaries
- The formatting of live conversation summaries

## Adding Copilot Summaries to Custom Case Froms

Add the msdyn_CopilotCaseSummaryLibrary web resource to the form. Then find the
control in components.

## Adding Copilot to Custom Apps

Go to Solution -> Add Existing Setting and add the Customer Service Copilot
Enabled Setting
