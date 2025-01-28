# SLAs and Entitlements

## SLAS

SLAs are used to halp organisations meet predefined service standards when
providing customer support.

An SLA is a container for any number of SLA Items. The SLA items are the primary
source of logic for this functionality.

### SLA Items

When we define an SLA item, the main items to be aware of are:

- Name: required
- KPI: required
- Conditions for when the item will apply
- Conditions for when the item has been met
- Pause and fail durations

An example would be that the item:

- Applies when the user has a gold service level
- Has been met when the case has been resolved
- Warning at 30mins and fail at 1hr

##### Other configurations

There are a few other configurations:

- Business hours
- Allow pause and resume
- Custom pause conditions overiding entity level conditions
- Actions to take for:
  - Near non-compliance (warning)
  - Non-Compliance (fail)
  - Success

We can define multiple items. The first rule which applies will be used.

### KPIs

A KPI defines another important piece of logic for an SLA Item.

We need a name, the entity it applies to, and the KPI field. The KPI field is
just a column with a 1:many relationship with the KPI instance table.

The main logic we define here is the Applicable From field. This deterines the
starting point of a KPI, there are various options here e.g.:

- Created on
- Escalated on

By default, only case is set-up for SLAs. To enable other tables, including
custom tables:

- Enable Setting up Service Level Agreements in the table's properties
- Create one or more KPI fields which are lookup fields to the SLA KPI Instance
  table

### Actions

These are just Power Automate flows. As with Case Creation, we get a template
which we should mostly leave alone. We can add actions for each of the three
states mentioned above.

### Calenders and Working Hours

There are two records we can define. Both are specific to SLAs. These are:

- Holiday Calender
- Customer Service Calender

The Customer Service Calender defines the regular days and times that customer
service is available. We can have multiple calenders for locations, service
levels etc.

The holiday calender can be used to define exceptions to the standard hours and
may be attached to a customer service calender.

We can optionally attach a customer service calender to an SLA Item.

### Pause and Resume SLAs

We may want the timer for an SLA to pause at certain stages, for instance on
hold or waiting for information. We can achieve this by specifying the status
reasons where the timer is paused. We do this from:

Admin Center -> Service Terms - Other SLA Settings

We can override this in a given SLA item to specify custom conditions.

### Application of SLAs

- If there is no entitlement with an associated SLA linked to the case:
  - If a default SLA exists this will apply
  - else no SLA will apply
- Else
  - The entitlement associated with the applicable entitlement will apply

### Adding an SLA Timer to a Form

This is very simple. Just search components within the relevant form.

## Entitlements

Entitlements are used to manage the support customers are entitled to.

The main elements are:

- Start and End date
- Restrict based on terms: Whether terms may be exceeded
- SLA: We can optionally specify an SLA to apply
- Entitlement Terms
- Entitlement Channels
- Products
- Contacts

### Defining an Entitlement

#### Entitlement Terms

Here we define what is an allocation unit? It may be number of cases or number
of hours. Once, we have that, at what point do we decrease the balance? This may
be on case creation or resolution.

- If case creation is the unit then the decrease is best defined as at the point
  of creation.

- If hours are the unit, then we should use resolution as the decrease remaining
  on.

This is particularly important where restrict based on entitlement terms is set
to true.

Finally, we need to specify the number of allocation units are available in the
entitlement. This is the total terms field.

#### Entitlement Channels

When we define a channel, we limit the number of cases for that channel only.
If we wanted a phone only channel we cannot simply set phone to 20. We would
need to also set all other channels to 0.

#### Products and Contacts

By default, an entitlement is available for all products and contacts related
to the primary customer. If we specify a product or contact then only cases with
the relevant product or contact can have the entitlement applied.

It does appear to create a case where no contact or product is defined. It will
throw an error if an invalid contact or product is defined.

Note, for contacts, having a primary contact is not enough. To add a contact
to a case you must go to the related contacts for the account and add the
relevant contact.

Note also that this is a blunt instrument, if you want to specify contacts for
a specific product or channel, for instance, you would need multiple
entitlements to be defined.

### Entitlement Templates

These are defined in Admin Center -> Service Terms -> Entitlement Templates.
They useful way to prepopulate values in an entitlement.

We do not specify a customer or contacts. But we can specify products and
channels.
