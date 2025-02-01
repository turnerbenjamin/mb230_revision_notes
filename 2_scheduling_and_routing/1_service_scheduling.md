# Service Scheduling

## Introduction

Dynamics uses the Universal Resource Scheduling Solution from D365. 

## Services

These represent services offered to users. It is responsible fo determining
the resources required of a given type.

### Resource Requirements

These are a tab on the service record. They define the items needed to create
a booking for the service.

We can add requirements and subgroups within individual requirements. A group
may require all or any of the requirements in a subgroup.

We can specify various things such as:
- duration
- part of same organisation
- fulfillment preferences
- organisational unit
- categories
- characteristics
- sort option
- effort required

Requirements are run in order and the first matching rule applies.

Effort can be used where multiple of one requirement is needed. For instance, 
If effort is defined as 2 and we have two technicians with a capacity of 1, this 
will translate to 2 technicians being required.

## Resources (Bookable Resources)

Resources, a.k.a. Bookable Resource is a broad category of resources that may be
scheduled. It includes:
- People
- Faclilities
- Equipment

### Facilities and Equipment

There are non-human resources. As with other resources, these may be associated
with a business unit and organisational unit. We can also define work hours for
these resources.

When we select these types, we must also specify a record for the facility or 
equipment. We can define these in Admin Center. 

It looks like we need a 1-1 mapping betweein facility/equipment records and
bookable resources of these types. I.e. if we create a crane equipment 
record, this may only be mapped to one bookable resource instance.

### Other Resource Types

- User: Dynamics 365 user
- Generic: Placeholder
- Contact: Dynamics 365 contact
- Account: Dynamics 365 account
- Pool: A group or resources
- Crew: Another type of resource group

### Work Hours and Business Closures

We can specify work hours for bookable resources. When defining a series of work
hours we can also specify whether or not business closures are observed.

We can also define breaks when defining work hours.

Business closures, for scheduling, may be defined in the service scheduling
section of Customer Service -> Admin

This seems unrelated to the calender items such as operating hours and holiday
calenders.

By default, the work hours are set to 24/7 with no business closure observation.

We can also specify a resource's capacity in the work hours. This is specified
as an integer. 

### Resource Characteristics and Proficiency Models

Characteristics may be either skills or certificates, out-of-the-box. We can add 
additional options here.

We can create new charateristics, we can add these characteristics to resources.

When we add a characteristic to a resource, we can optionally, specify a 
proficiency level. We can also define proficiency models to use here.

### Resource Categories

These are used to group bookable resources by type. Rather than requiring Joe
Blogs, a technician for a service, we relate Joe Blogs to the technician 
resource category. It is the category we use in the resource requirements.

We can provide for a prefered resource in the resource requirements which will
be a specific resource instance like Joe Blogs.

It looks like a single bookable resource may be associated with multiple 
resource categories. 


### Organisation Units

Organisational units are another means for grouping bookable resources. 

At its most basic, an organisational unit can be defined with a name only. 
However we can also define a logitude and latitude. 

When we define resources, we must define a start and end location for that 
resource. One way of defining a location is to use the organisation unit. In 
this instance, the organisational unit must have both longitude and latitude
defined.

If we do not use an organisational unit to define a location, the organisation
unit field of a resource is optional.

NOTE: While both organisational unit and location for the unit may be 
optional, it appears that Universal Resource Scheduling will only work if both
have been set.

## Fulfillment Preferences

Resources are scheduled using the schedule assistant. Potential resources are 
displayed based on:
- Resource schedules
- Earliest available time

Fulfiment preferences have two features:

### Intervals

Intervals define the duration between time slots. 
- We can define the interval between available starts, e.g. 1hr
- We can define when intervals begin (if blank this will be the time of the
booking, e.g. 12:13, 13:13)
- We can also define results pre interval which is the number of resources we
will show for each interval, e.g. if 50 results, show only the first 5.
- There is also an option to reset intervals per time group detail. Here 
intervals start from the start of each time group. 

### Time Groups

These are defined in the details time.
These can define the time in which intervals may occur. For instance, we may 
have a 9:00-17:30 workday with a 30 minute break at 13:00. Here, with 1hr 
intervals, and the intervals being reset we get the following start times
- 9:00
- 10:00
- 11:00
- 12:00

- 13:30
- 14:30
- 15:30
- 16:30

We can attach fulfillment preferences to resource requirements within a service.

If we use time groups, we cannot specify a time for intervals begin. This will
automatically be the start of the earliest time group.

## Booking

A booking contains information for a given booking, such as the resources 
assigned to the booking, estimated vs actual times and total time spent on the
item

## Scheduling Service Roles

The two current security roles specific to scheduling are:
- Customer Service Schedule Administrator
- Customer Service Scheduler

## Create Service Activities

We can create a new service activity from the Activities grid in both Hub and
Workspace.

We can also configure the timeline to allow a service activity to be created
from there, but this is not available by default.

Once a service activity has been created we can use the book button to create
a booking. This will open the scheduler assistant.

## The Schedule Board

This is an interface where we can view scheduled Activities. There is a some 
detail about how this works in the guide. 













