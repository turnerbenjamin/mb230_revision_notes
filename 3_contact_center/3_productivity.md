# Productivity

## Quick Replies and Email Templates

These are both methods to help agents send common messages to customers quickly.
In both instances:

- Agents can create their own personal templates
- We can use Insert Dynamic Text to quickly add slugs.

In the case of quick replies we can also add tags to help agents find the item.

By default, quick replies are available organisation wide. If we add a quick
reply to one or more workstreams it will only be available in those workstreams.

## Macros

Macros are similar to Power Automate flows. They may be created and then
triggered by agents, generally through an Agent Script.

We can use slugs, as with quick replies, but we must research these.

To debug a macro, as with Automate Flows, we can look at the run history and
open a run to see details of the paths taken, variable values and where the
error occured.

## Scripts and Slugs

Scripts can be used to provide guidance to agents. They can be:

- Text
- Macro
- Nested Script

These are accessed through the productivity pane. To use these the pane must be
enabled with agent scripts and the script sould be added to a session template.

## Smart Assist

Smart assist can be used to provid AI recommendations to agents to help them
identify similar cases and knowledge articles.

To enable smart assiste we need:

- Productivity tools installed in the environment
- To enable smart assist in Insights
- To enable smart assist in the productivity pane

We can customise this basic behaviour by adding Data Mapping rules for cases and
knowledge articles.

If futher customisation is needed then we may deploy a smart assist bot.
We would:

- Build a bot with Azure Bot Services
- Create a bot user in Admin Center -> Bots
- Add to bot to a workstream in the Smart Assist Bots section

## Automation Dictionary

This is used to hold context data for sessions. We can interact with it using
slugs, oData queries or static values. The Automation Dictionary is able to pull
data from a range of sources.
