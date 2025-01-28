# Manage Collaboration

## Teams

### Enable Teams Chat

We can enable Teams Chat in Customer Service from Admin Center -> Collaboration
-> Embedded Chat using Teams

#### linking Records to Teams Channels

This option permists people in the org to connect records and views to Teams
channels and open records in Teams during meetings

There are two additional options related to this:

- Enhanced Integration: Allows for records and views to be pinned to a channels
  from within 365 and suggest members to be added
- Confidential Labels: Sensitivity/Confidentiality labels may be added and
  private teams channels created.

#### App Access to Teams Chat

We can enable teams chat for all D365 apps or selected 365 apps

#### User Access to Teams Chat

All default Agent Experience Profiles will have embedded teams chat enabled by
default. For custom profiles we can enable this in the productivity pane
section.

#### Embedded Teams Chat Record Configuration

We can add record types to a list of records that may be connected to Teams
chat. For each we can configure various fields such as:

- Automatic naming of chats
- Who can disconnect chats
- AI and Rules-based contact suggestions

### Enable Teams meetings

This is set-up from Admin Center -> Collaboration -> Meeting Integration using
Teams

For this to work we need to:

- Sync Teams and Outlook calenders on the back-end
- Enable End users can add and join Teams meetings from appointments in
  model-driven apps from the settings of the environment.

## Swarming

Swarming is not explicitly covered in the learning materials but we will cover
it briefly here.

### Swarming Prerequisites

To set-up swarming we need:

- Embedded chat for teams to be turned on
- Activate case details on swarms
- Turn on the swarm expert notification in Power Automate

This is all very simple and, other than the first requirement, can be done from
Admin Center -> Collaboration -> Customer Support Swarming

The second requirement relates to activating the Case form for swarming Form. We
can of course customise this if we wish.

### Swarming Resources

We need to have bookable resources and skills set-up to use swarming. An
important benefit here is that we can create a record without a user account so
an expert need not be a user.

### Determine Skills Required

The condition rules section allows us to specify conditions using the swarm
request and related entities (e.g. case), to add required skills to a given
swarm request. We can add up to 100 rules.

### Swarm Guide

This is a simple guide that we can write which will help users when writing
their request to help when recommending skills.

### Automatic Participants

We need at least 2 participants for a swarm, we can add people like the team
admin and manager automatically.

### Create a Swarm

Once set-up, agents can select Create Swarm from the command bar and create
their swarm request. The guide will be shown in this form by default.

Users can also manually add up to 10 skills required for the request.

### Swarm Process

Once a request is made the system will find a minimum set of experts covering as
many skills as possible and send them a notification to join the swarm. Experts
will receive the request as an adaptive card and will be able to either accept
or reject the invitation.
