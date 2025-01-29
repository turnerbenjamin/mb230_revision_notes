# Customer Voice

## Introduction

Customer Voice is a survey tool used to capture and analize feedback. Reports 
are enriched with graphics powered by Power BI.

Data, including:
- surveys
- questions
- invitations
- responses

is stored in the Dataverse.

## Projects

Projects are containers for surveys and associated reports. These are created
within a specific environment. The environment must be either Production or 
Sandbox.

## Building A Survey

### Templates

When building a survey we can select from a template. This can be useful when
learning how to use the tool.

### Question Types

Surveys can contain a variety of question types:

- Choice
- Date
- Likert
- Ranking
- Rating
- Text
- Net Promoter Score

A survey may include up to 100 questions. With Likert, choice and ranking 
questions, each option counts as an individual question.

### Branding

We can customise the survey to align with the organisation's branding. There are
a lot of options here.

### Branching Logic

#### Simple Logic

There are simple logic controls:
- Display logic: e.g. display if value less than 7
- Skip Logic: e.g. skip if greater than 6

#### Advanced Logic

If the simple logic controls are not sufficient we can also use advanced logic,
this involves specifying conditions and actions. Actions are composed from:

- Target type (question, sections, end of survey, url)
- Target value (e.g. a specific section or question)
- Visual actions (shoe, hide, navigate to)

The best practice for display logic is to hide by default and display if 
conditions are met.

We would still need a hide action as a condition may become false after a 
change in the form.

### Variables

We can add up to 15 variables within a survey. We must declare both an 
identifier and a default value when defining these.

Variable values are passed with the survey link and returned with the response.

By default, there are three variables:
- First name: cannot be deleted
- Last name: cannot be deleted
- Locale: may be deleted

Variables, other than first and last name, need to be populated with Power
Automate. I assume that first and last name can be derived from an email contact
when the survey is sent by email.

### Reports

#### Satisfaction Metrics

When we create a survey, several items will be added to the reports section
automatically; this includes a Satisfaction Metrics report.

This report will be blank until metrics have been added. The metrics can be
shown at 3 levels:
- project
- survey
- response

We can add up to 10 metrics per project

##### Satisfaction Metric Types

- NPS (0-6 detractor, 7-8 passive, 9-10 promoter)
- Sentiment: Calculated from text questions
- CSAT: Calculated from ratings questions

The satisfaction metrics for a survey can be accessed from the customisation
menu. We can map metrics to questions.

Note, metrics belong to the project. Changing the name of a metric will change
the name for all surveys using them within the project.

#### Survey Distribution Overview

This is found from the send tab on a survey and shows a breakdown of invites,
responses, unsubscribes etc.

#### Survey Response Report

This contains data and visualisations for responses to each question is a 
survey.

#### Custom Power BI Reports

We can create custom reports using Power BI. It looks like we need:
- Power BI Pro (licence)
- Power BI Desktop (tool to create the report)

Voice data, as mentioned, is stored in the Dataverse. We can use the Power 
Platform connector and select Common Data Service.

Once connected to the environment, we can access the relevant tables, this will
be those prefixed with msfp which stands for MS Forms Pro. 

We could use this to generate visuals, e.g. for NPS:

%Promoters - %Detractors

### Alerts

We can create alert triggers, for instance, if an NPS question is responded to
with a value less than 7.


## Languages/Translation

As with knowlege articles. Translation must be performed manually, however, 
there are tools to help with the process. 

40 languages are available out of the box, we may add up to 80 languages by
defining a display name code for the language.

Where different languages are available, we may optionally enable the ability of
respondants to change the language used from a drop-down menu.

A language may be set by:
- Using Power Automate to set the locale
- Custom survey links which pass the lang in a query string
- Browser language setting
- The respondant where enabled

## Sending Surveys

### Email

We are able to send surveys by email using Customer Voice. This is achieved by
defining Email Templates. These may include variables to personalise the 
content.

Templates must include:
- A survey link
- An unsubscribe link

We can include the first question in the survey within the email. This must be:
- Choice (single answer)
- Rating
- NPS

Email Templates are user scoped but may be shared.

It looks like there will be a default template for all surveys.

#### Email Translations

There is a language option that allows us to provide translations for a given 
survey. Where a specific language template is sent, the survey will use the same
language if available to maintain consistency.

#### Reporting

We can view reports to see invites sent, responses, unsubscribes etc.

#### Adding Contacts

We can quickly add contacts for a survey with a CSV file. We may import up to
10,0000 recipients at once. 

We can also associate an invitation and responde in the same environment using
additional columns in thye csv:

- Regarding Id: Table to associate with the invitation and response
- RegardingTableName: Name of the above table

### Links and QR Codes

These methods are useful if the surveys are to anonomous users. We should design
surveys sent by this method with this in mind.

If the survey is set to allow only internal respondants, name will be captured
as they must be signed in to respond. 

We can attach variables to the link (query string)

### Power Automate

Power Automate is a particularly powerful method for sending survey invites. As
we can trigger them at moments of truth, such as after a case has been 
completed.

We can create a flow from the send tab of a survey. As with automatic case
creation, this will provide us with a template.

In this instance, it looks like we may select from a range of templates for 
different triggers.

We can also pass variables from a flow to the survey, for instance, we may have
a language choice column associated with a contact. This may be used to set the
locale parameter in a flow.

### Variables in a Response

Variables are used to customise a survey. But they are also passed through to
the response record where they may be retrieved and used.

We can use flows here to run when a survey runs, access and parse the Context 
data and use it.

### Embedded Surveys

A survey may be embedded in a website. There are three formats we may choose
from:

- Inline
- Pop up
- Button, which when clicked, expands to display the survey

When we use this method a script tag will be generated, similar to widgets.

We can customise the variables that we want to capture and populate these in 
code by passing these as arguments to the render survey method.



