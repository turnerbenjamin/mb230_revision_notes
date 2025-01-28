# Workspaces

## Agent Experience Profiles

These allow us to provide customised experiences for different user groups
without having to build a custom app.

There are various default profiles out of the box. We cannot edit these. We can
easily create our own profiles and add users to them.

## Inbox Views

We can create custom views within the inbox in workspaces. This is a simple
process. Each view may contain multiple record types.

For each record type we can use simple or advanced filters.

We can also provide a single sorting rule for records.

The suggested actions view is readonly and may not be removed. We can disable
it from the Copilot AI Features panel of the profile.

## Session Templates

Session templates may have a generic type or an entity type. Generic types will
be used as the default where no other type is specified. These are attached to
a workstream.

Entity types are attached to Agent Experience profiles for their type.

Entity types have an anchor tab which may not be customised. With generic types
we must specify the anchor tab.

## Application Templates

Application tab templates may be created and associated with a session template.
This can be used to automatically add context for a given record.

There are various types, each with their own parameters. Depending on the type
we will need to populate one or more of these parameters for the form to work.
This is achieved using slugs.

## Notification Templates

These are used to control the content of notifications shown to agents and their
behaviour.

In terms of behaviour, the main options to look at are auto-assign which stops
the agent from rejecting the notivication. And the timeout option.

We can also specify whether desktop notifications should be shown.

In terms of content, we use notification fields. There are a variety of
predefined fields we can use, we may also define our own. But we should consider
whether the data will be available in the context the notification is designed
for.

We can also define some behaviours globally for all notifications:

- Status change on missed or rejected notifications
- Sounds
