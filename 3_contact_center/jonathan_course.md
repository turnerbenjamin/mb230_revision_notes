# Notes from Jonathan's Lesson

## Deploy Contact Center

In Admin Center -> Home there is a create Contact Center button. This
has a guide to start setting up the center.

It looks like this, amongst other things, sets up a chat channel with
various items.

## Workstreams

These are a way to organise and route incoming work. These include:

- Name
- Type
- Channel
- Work Distribution (push/pick)
- Routing rules (classification, routing rules, fallback queue)

Workstreams must have at least one channel

### Work Distribution

#### Capacity and Presence

This represents how much time it takes of an agent's time. These can be
specified for all work items. This is used to determine who has the capacity to
work on an item.

Presence specifies which status items are equated with available to work.

## User Profiles and Skills

We can specify skills from the User Settings. These can be associated with users
and used to determine who has the requisite skills to complete a given item.

For a skill we only need to give a name, type and description. There are two
types:

- skill
- certification

Capacity profiles can be used in place of unit based capacity management. We can
manage these from Skills Hub in Admin Center -> User Settings -> Skills Hub

All work is based on units. However, with this method we can assign users a
given capacity profile. This can specify for those users the their work limit.

I think

### Proficiency Scale

Here we can define a scale we want to use to measure a user's proficiency in a
given skill.

### Intelligent Skill Finder Models

These are models we can train by feeding it data. It will look at past items and
skills needed to try and predict required skills for future items.

We can get this data by specifying filters and date ranges.

## Chat Channel Configuration

A channel needs a workstream. We can use an existing workstream or set up a new
one

### Chat Widget

Here we can customise the widget. This includes the look of the channel and some
behaviours such as:

- Proactive Chat
- Reconnect previous chat
- Show widget only in operation hours
- Only show widget on specified domains

### Behaviors

Here we can specify automated messages these need a:

- Trigger
- Message
- Status

There are various triggers here.

We can also configure pre and post conversation surveys. The post survey seems
to use Customer Voice

We can also use auth settings, this can be used to authenticate users before
the case.

There are user messages, such as showing position in queue and average wait
time.

There is also location settings.

Many of these settings

### user Features

These relate to user functionality, such as:

- File attachments
- Customer Notifications Settings
- Transcript availability
- Ability to switch to voice/video calls
- Screen sharing
- Co-browse

### Adding a Widget

We can add a widget to a power aps page. Go to:

Make.powerapps -> Content -> Content Snippets and add the code. We can also
include conditional rendering within this.

## Proactive Chat

Uses rules to automatically send notifications to users. I think we need to have
a more detailed look into this.

## SMS Channel

The functionality must be enabled, I think this is with the Omnichannel install.

We must have an SMS number registered with a supported provider. Currently only
Twilio I think.

## Voice Channel

Very similar to the above. There is an extra step with this channel. We can also
edit things like the plan and the settings of a number as long as it is not
currently associated with an active workstream.

It looks like calls go to queus which are then picked up by the channel and then
the workstream for distribution. When setting this up there is a group number
value which is an integer. This is just for our use to organise the queues as
we like (In the list). We may have priority based queues, language based queues
etc.

We can define things like hnold music, bot voice, bot speaking speed, wait time
and position notifications etc. Whether transfers are enabled etc.

## Not Covered

This presentation has not covered setting up Digital Channels.
