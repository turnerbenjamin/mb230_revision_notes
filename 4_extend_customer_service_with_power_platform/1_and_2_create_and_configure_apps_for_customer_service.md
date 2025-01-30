# Create and Configure Apps for Customer Service

## Intro to the Power Platform

Power platform is a suite containing Apps, services, connectors and a data 
platform. There are 5 core products:

- Power Apps
- Power Automate
- Power BI
- Power Pages
- Microsoft Copilot Studio

## Core Concepts

### Dataverse

The Dataverse is a cloud-based, low-code, data service and app platform. It 
connects to all other aspects of Power Platrform. Features include:

- Security: authentication uses MS Entra ID. Authentification may be configured
down to the row and column level
- Logic: Business logic may be applied, e.g. duplicate detection and business
rules
- Data: We can model, validate and report on data
- Storage: Data is stored in Azure cloud
- Integration: We can connect to the dataverse with APIS, webhooks etc

### Connectors

Connectors are used to create a bridge from a data source to an app or workflow.
There is a connector for Dataverse which allows Power Apps to access the data 
used in Customer Service.

## Power Apps

### Canvas Apps

Canvas Apps are built around user experience. We can connect to a wide-range
of data sources, including Dataverse. 

These are very customisable and particularly useful for task-orientated Apps

### Model-Driven Apps

Model-Driven Apps are built around the Data model. They comprise forms views 
and other components tied to tables in the Dataverse.

There is less control over the components in a model driven app. 

It is possible to emabed a canvas app on a model-driven form. This can be useful
if we want to:

- Display data from various sources next to data from Dataverse
- Use and update data from other sources
- Interact with data in fields on the model driven app form
- Trigger Power Automated flows from buttons in the embeded canvas app
- Perform complex logic not posible in modern driven app forms without coding
- Create a wizared-like UI to guide the user through a complex set of decisions
based on data

## Customise Case Management

### Remove the Contact/Customer Validation Rule

We have seen this already. Find the msdyn_IncidentShouldValidatePrimaryContact 
environment variable in the solution and set the value to 0.

### Allow Updates for Resolved and Canceled Cases

Customer Service Admin -> Service Terms -> Other Settings

There is an Allow updates for setting with the following options:

- Don't allow updates
- Resolved cases
- Cancelled cases
- Resolved and Cancelled cases

### Modify the Case Resolution Dialog

The case resolution form does not allow for the creation of new forms. There 
are the following forms out of the box:

- Main
- Quick Create
- Quick View
- Card

Although we cannot create a new form, we may edit the existing forms.

Control over the form shown on case resolution can be found, in the same place
as the previous setting:

Customer Service Admin -> Service Terms -> Other Settings

The options for this setting are:

#### Standard Dialog

This looks like the default main form. It has only resolution type and 
resolution. Modifications to the main form do not have an effect here.

#### Quick Create Dialog

This opens the quick create form to the side. Modifications to the quick create
form are applied

#### Customisable Dialog

This opens the main form as customised.

### Add Custom Values to the Case Resolution Dialog

This is a headache:

- If we use the standard dialog, the resolution type is drawn from the status
reasons choice column on the case table
- If we use a custom dialog, the resolution type is drawn from the resolution
type choice column of the case resolution table

If we add a new reason to the case table only. This will only show if the 
standard dialog is used. We can select the custom value without error

If we add a new reason to the case resolution table only, then this will only
show if the custom dialog is used. However, if we select the custom value we
will get an error on save.

Accordingly, if we are using a custom reason we need to either:
- Use the standard case dialog
- Ensure that both the case and case resolution table's status reasons are 
aligned



















