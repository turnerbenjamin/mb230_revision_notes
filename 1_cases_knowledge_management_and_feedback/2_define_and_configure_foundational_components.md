# Define and Configure Foundational Components

## Implement Advanced Similarity rules

Without using smart assist. We can use the similar cases button from the Cases
for Interactive Experience Form.

This will only work once we set-up advanced similarity rules. These can be set-
up from Admin Center -> Case Settings -> Advanced Similarity Rules. it is very
simple.

## Implement record creation and update rules

We can create a rule with a name and an activity type to monitor. Optionally, we
may also specify a queue to monitor to further filter activities received as an
input.

We can also define whether we want to send an automatic reply when the case is
created with an email template.

Once saved, we can specify rules for case creation. These may be used to
populate fields based on the activity record. This can be helpful later for
routing. We do this by customising the Power Automate flow attached to the rule.

Depending on the record type being monitored, we may have additional settings.
For email, we can specify whether we will allow emails from unknown senders, and
if so, how we handle this.

### Activity Monitor

This can be really useful for reviewing activities and how they were handled.

## Configure and modify the Case Resolution dialogue

In essence we just need to:

- Go to Admin Center -> Case Settings -> Other Settings and set resolved case
  dialogue to customisable
- Edit the form for the Case Resolution Table in make.powerapps

## Configure business process flows

### Configure Existing Flow

1. Go to the solution in make.powerapps
2. Search for the flow, select it and click edit

### New Flow

1. Go to the solution in make.powerapps
2. Select New -> Automation -> Process -> Business process flow
3. Add a name and an entity type for your process (Letter)
4. Once saved open the Business Process Flow
5. Build your flow
6. Activate the flow
7. Select edit security roles, find the role and in the
   business process flows tab enable necessary permissions
8. From the app pop-up, click the ... for Hub and select Open in App Designer
9. In the automate tab add your flow
10. Save and publish
11. Test in Hub

## Configure and manage security roles and personas

Too familiar with this to care

## Configure enhanced case forms and views

These can be enabled from Admin Center -> Case Settings -> Enhanced Case
Experience. In both cases, a configure link will take us to the form in
make.powerapps.

With both forms we get:

- Adding quick notes
- Colored priority tags
- View of customer details and recent cases in the same form
- Attachments can be easily added.

The Enhanced Case Form will also show SLA timers where applicable once saved.

Note, this form will be seen without being enabled if it is at the top of the
case forms list in make.powerapps.

### Usage of Enahanced Quick Case Form

When we select Create Case from an AI summary of a conversation, the Enahanced
Quick Case Form will be opened in a panel in the same screen. Many of the fields
will be prepopulated based on the summary.

We can add attachment and quick notes before saving the form

### Usage of Enhanced Full Case Form

This is a full screen form, but as we populate the customer, a pane will
automatically be opened to show customer information in a card with details and
recent cases.

## Configure the records displayed in the case timeline

Too familiar with this to care

## Configure connectors with the timeline

This is used to allow developers to surface information like Dataverse table
rows and external data sources as record entities within the
TimelineWallControl component.

We need to first define a connector. Connectors are a JS webresource containing
the definition of the control. The resource needs to conform to the
IRecordSource interface.

Once defined, we can add the connector to a timeline by finding the component
within a form in make.poweraps, selecting it and selecting add connector.

We need to provide a constructor and a resource path. Optionally, we can also
include a configuration path.

## Configure the timeline and cards on custom forms - Nasmin

## Enable AI suggestions for similar cases - Remel

Smart assist makes AI-based recomendations to agents. This can be used by agents
to:

- Identify similar cases
- Identify relevant knowledge articles
- Identify any other entities the bot is programmed to look for

### Enabling Smart Assist

The first prerequisite is that productivity tools are in the environment. This
is deployed for most new deployments. If it is not deployed we can install the
Productivity Tools app to the environment.

To confirm that the tools are deployed we can navigate to Admin Center ->
Productivity -> Productivity Tools. This should contain a record for smart
assist.

Next, we need to enable smart assist. This is done through Admin Center ->
Insights. We cannot access this in the trial, but it looks like there is a
section for suggestions for agents. In this we enable similar case suggestions
and knowledge article suggestions.

Finally, smart assist is accessed through the productivity pane. We need to
ensure that this is enabled in the relevant Agent Experience Profiles and that
smart assist has been turned on.

### Testing Smart Assist (Activity)

1. As a customer, initiate a conversation with chat
2. Accept the conversation in Workspaces
3. Open smart assist from the productivity panel
4. As a customer write: I am having trouble with my Contoso SmartBrew 3000
5. The smart assist panel should automatically update to find related articles

### Smart Assist for Similar Cases and Knowledge Articles

In the example above we use smart assist for similar cases and knowledge
articles. For this use case, we do not need to create custom bots. Suggestions
are powered by pretrained models.

We can customise the behavior of smart assist here in:

Admin Center -> Insights -> Suggestions for Representatives

As mentioned above, there are toggles to enable both similar case suggestions
and knowledge article suggestions. There is also a Data Mapping Section.

#### Data Mapping

In the data mapping, we can customise the fields used to make suggestions for
both cases and knowledge articles.

By default, cases are suggested based on the case title and description. We can
add up to three more fields for the model to use when making suggestions.

For knowledge articles, title and content are used by default. Again we can
choose up to three different fields to use for comparison, e.g. keywords.
