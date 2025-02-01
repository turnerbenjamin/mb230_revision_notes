# Routing

## Intro

There are two main routing options:

### Unified Routing

This is can be configured to automatically direct work to the best queue and 
agent based on requirements. While basic routing applies to records, unified 
routing applies to allo channels.

There are two main stages:
- Classification: Information, e.g. required skills and importance is added to 
the item
- Assignment: Work is assigned to agents

### Basic Routing

Basic routing is a more basic feature used with records only. 

The main feature here is the Basic Routing Rule Sets. These simply define a set
of conditions. If the conditions are met then the item will be routed to the
appropriate queue.

These rules will be applied when:
- The save and route button is used
- When a case is created automatically

## Set-Up Unified Routing

We can enable unified routing in Admin Center. We also need, at a bear minimum
users to route items to.

## User Set-Up

Users will need a security role that enables them to be added to an advanced 
queue, e.g. Customer Service Representative. 

Within the Omnichannel Tab of a user's record there is a variety of options 
related to unified routing. For instance, default presentce and capacity.

Where capacity is used, each channel will have a set number of units for each
work item, e.g. 25 effort. A user will have a default capacity of 100. So they
may take up to 4 items from that channel.

Capacity here is different from that related to a bookable resource and the 
effort defined in a resource requirement.

### Bookable Resources

Features such as skills-based routing require that a bookable resource record
has been set-up for the agent. We can use this resource to associate 
characteristics with that agent.

## Queues

In a workstream, work classification and route to queue rules are used to route
an item to the appropriate queue.

Once in a queue we can set up rules used to assign items to members of that 
queue.

### Queue Set-Up

For Unified Routing, we need to use advanced queues. These have a number of 
options not available in a basic queue:

#### Assignment Method

This option determines how work should be distributed between agents with the
requisite skills and availability, the options are:

- Highest capacity
- Round Robin
- Custom

When defining custom rules we need to define:

- Prioritisation: The order in which items are assigned. Each rule represents a 
priority category. Categories at the top get the highest priority.
- Assignment: Conditions used to select agents. There is also an order by option
to sort matching agents where more than 1 agent meets the conditions. If no
agents maych the next rule is evaluated.

We should use skill matching rules in custom assignment methods where used. The
default skill matching algotithm settings will not be used in a custom 
assignment method.

#### Operation Hours

The operation hours for a queue may be set

####  Overflow Handling

We can define rules to divert work to a different queue when:
- The queue is out of operating hours
- Wait time in the queue exceeds a given value

## Workstreams

A workstream is just a container used to enrich and route work items. Work comes
in from a channel it is then:

- Enriched with work classification rules
- Routed with route to queue rules

### Work Classification

These are rules used to add information to work items. For instance, we may 
define conditions, which if met, add a required skill to an item. This 
information may then be used, e.g. in route to queue rules and for skills-based 
routing.

We are essentially looking at unstructured data here and trying to add pieces
of structured data we can use to optimise routing.

We can create up to 10 rulesets for work classification in each workstream.

For each set of rules, the rules are run in order and the first matching rule
is applied.

Values set in an earlier ruleset may be used in later rule sets.

These rules may be:
- Logical rules with defined conditions and results
- ML Models
    - Skill identification
    - Sentiment prediction
    - Effort estimation

#### Logical Rules

These simply define conditions and outputs.

It looks like our output may set:
- Attibutes (skills, capacity profile, customer, escalation count, issue)
- Related Entities (e.g. email record, account, contact)

There are different outputs depending on the item associated with the 
workstream, e.g. chat or email.

#### Machine Learning Models

#### Sentiment Prediction

This will evaluate sentiment based on messages sent by the customer. The model 
will assign a sentiment value from very negative to very positive on a 7 point
scale.

Unlike the other options, this uses an out of the box model. 

We can select 1-10 attributes to be used by the ML model. These must be 
accessible from the work item. 

For a record, e.g. case, description is a useful attribute to use
For a messaging chanel, such a case, the Context Item Value (Conversation)
should be used.

With a chat, bot context variables, or a pre-conversation survey should be set
up to use the input attribute. 

#### Effort Estimation

With effort based routing we need to build a model. This is done in 
Admin Center -> Routing -> Effort Estimation Models.

We need to define the fields that the model should look at (minimum of 2
attributes).

We also need to define the calculation of effort. We can use a single field, a
KPI instance or a calculated duration in which we provide a field to use for the
start and end time.

Finally, we can provide a filters to limit the data used by the model. This can
be done with conditions, and there is a separate section with a date range 
filter.

Training takes some time, typically 2-3 hours.

The outputs of the model are:
- Effort value (minutes)
- Effort Confidence Score

Once this has been set up we can use it in a work classification ruleset.

#### Inteligent Skill Finder

This is similar to the above. We need to first create a model. We do not have a 
section for effort calculation here, I assume it just looks at skills manually 
applied.

We should aim for at least 50 records to train the model and should periodically
retrain the model.

There is the option to import training data in an Excel file.

### Route to Queue Rules

The interface for defining these rules is not unlike that used for basic routing
rules. 

We can only define one route to queue ruleset per workstream.

If no route to queue rules apply, the default will be used.

### Work Distribution Mode

The modes here are:

- Push: Auto-assignment to agents
- Pick: Agents may select items to work on

We can also set the capacity mode, this may be unit based with each item 
consuming a fixed number of units, or profile based where each work item can be
associated with a capacity profile.

Define capacity profiles in Admin Center -> User Management -> Capacity Profiles

Here we can specify the total work items a user can have. We can also enable 
assignment blocking which transitions presence to DND when the max limit is
reached.

We can attach capacity profiles to users and define capacity here



### Intake Rules and Channels

For voice and messaging items, the workstream will have a dedicated channel 
serving as the input for that workstream.

For records, there will instead be an intake rules section. These are defined
from Admin Center -> Routing -> Record Routing. 

These rules map to specific channels or routing rule sets.

## Skills-Based Routing

This is a feature available in unified routing. It does not appear to be a 
required feature.

This feature is relevant in the assignment section of the process. 

At a high level:

### Define Skills and Associate them with Users

#### Skill Definition

Skills may be defined from Admin Center -> User Management -> Skills

We can create skills from here and attach users. Note, these skills are used
generally, however, we will only see users attached to skills. A bookable 
resource attached to a contact for instance will not be displayed in a skill's
grid.

Skills are attached to users using a bookable resource record with the type of
user.

#### Rating Model Definition

When assigning a skill to a user, we need to assign a proficiency level. This
is done using rating models.

Rating models can be defined from Admin Center -> Routing -> Skills Based 
Routing

The recommendation is to use a 1-10 range to give flexibility.

NOTE: This form also has a control that allows users to update the skills
required for a given item.

## Skill Matching Algorithms

Skill matching algorithms are configured from the Work Distribution section of a
workstream. The options are:

- Exact Match
- Greater Match
- None

### Exact Match

- Looks for agents with minimum required proficiency, else
- Looks for agents with higher than required proficiency, else
- Item will be unassigned and must be selected from the queue

### Closest Skill Matching
- Exact match, else
- Higher match, else
- Less than match for all criteria
- Less than match for any on criteria
- Availability and capacity based matching

## Entity Record Routing

### Entity Set-Up

We can route any entities using record routing. We need to ensure that the 
table may be added to queues:

- Is an option when creating a new activity
- Can be added to a queue
- The option to move rows to the owner's default queue is not enabled

This is done from the advanced settings for that table in make.powerapps

### Record Routing Set-Up

Once our table is enabled for queues, we need to enable it for routing. This is
done by going to:

Admin Center -> Routing -> Set-Up Record Routing

We can add the entity to the list and then select it to configure the intake
rules. 
