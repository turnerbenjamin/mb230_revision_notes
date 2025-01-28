# Create and Manage Cases

## Introduction

This section will combine notes related to creating and managing cases. Since
this stuff is fundamental it will be limited to the more interesting points.

## Business Profile Flows

These are guided processes with different stages and steps to resolve a specific
item such as a case.

## Parent/Child Cases

We can create a parent child relationship between cases. Where this is set-up
we can:

- Define inherited fields
- Set-up cascading rules

- It can only be one level deep
- By default we can only associate 100 child cases with a parent

## Case Merging

Case merging is used to combine several cases, e.g. where there is a duplicate.
We can select the cases to merge and a primary case. The primary case will
remain active and receive timeline activities from the other cases. The other
cases will be cancelled with a reson of merged.

## using CoPilot to Assist in Resolving Customer issues

Copilot can be used by agents in a variety of contexts including:

- Ask questions
- Drafting content like emails
- Summaries, e.g. of timelines

## Status Reason Transitions

These are an optional feature allowing us to define what the status reason value
can be changed to for each status reason. This can help users to select the
correct transition.

When we define these, we must ensure that there is at lease one path to an
inactive status for any active status.

## Queues

There are three queue types in Dynamics 365:

- Public: Visible to the entire organisation
- Private: Visible to queue members
- Personal: Associated and visible to a specific user or team

A user can pick a work item from a queue. This will remove it from the queue and
add it to their personal queue. Once resolved it is removed from the queue.

If a user releases an item it will be returned to the queue from where it was
picked.

### Records and Queues

Out of the box queues are only preconfigured for:

- cases
- activities.

However, we can configure other tables to use queues. To do this we just find
the table in make power apps and enable the option , when rows are created or
assigned move them to the owner's default queue.

### Emails and Queues

Some queues have email aliases. This is required where the queue will receive
email. The alias must be associated with a working mailbox. The mailbox must be
approved and turned on.
