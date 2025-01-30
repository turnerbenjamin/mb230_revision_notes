# Implement Copilot for Customer Service

## Intro

This section seems to relate to custom bots, as opposed to custom smart bots.
These are used to provide quick support for simple issues. More complex problems
may be escalated to an agent.

## Prerequisites

We need licences for:
- Chat service
- Digital messaging
- Copilot studio
- Azure subscription

## High Level Steps

- Register an application in Azure
- Create a Copilot with Copilot studio
- Connect the Copilot to Customer Service
- Configure Customer Service

### Register an Application in Azure

Copilots are application users. Application users need to be registered in Azure
with an Entra ID. Once registered consider:

- Security roles required for the application
- Using certificates and secrets for authentication
- Access policies on resources

### Create a Copilot with Copilot Studio

When a copilot has been integrated, the full conversation and any variables 
captured may be shared with Customer Service. We should consider this ability
to capture and transfer data from the bot while designing it.

#### Topics

Topics generated from Historical Analytics, may be used as topics by Copilot 
Studio bots.

In Copilot, topics may be associated with trigger phrases. These are used to
understand when to trigger a topic.

Where a topic has been found, we can then have a question or series of 
questions.

#### Transfering to Customer Service

Copilot Studio has a conversation node called "End the Conversation". This node
has two options:

- End with survey
- Transfer to an agent

Copilot also needs to know where to transfer the conversation. This is done by
opening the manage node and configuring Agent Transfers. We will need to provide
the relevant environment and application id for the Customer Service Instance.

#### Content Display Issues

Note that there may be issues when transferring certain items such as:

- Emojis
- Certain Notes
- Certain variable types

Customer service may not be able to display these correctly. We should research
the limits of the integration when designing a custom bot.

### Connect the Copilot to Customer Service

To connect the bot to customer service we will need the Copilot extension for
customer service installed in our environment.

If we want to use the bot with voice channels we will also need:
- Copilot Studio Telephony Extension
- Omnichannel Power Virtual Agent Extension
- Omnichannel Voice Power Virtual Agent Extension

### Configure Customer Service

When we connect a copilot to Customer Service a virtual agent user should be 
created automatically. Conversations may be transferred to a virtual agent as
with any other user.

To route to a bot in customer service we just need to add the bot user to the
relevant workstream in the bot section

#### Context Variables

As noted, the bot will automatically transfer variables to the Customer Service
instance when a conversation is transfered. 

We need to ensure that any variables we wish to consume are declared in the
Context Variables section of the workstream.

Note, it is useful to include the va_Scope variable. This contains data which
may be particularly useful when routing as its presence indicates whether the
conversation has been transferred from a Bot. 

For instance, we may route to a human queue if this variable is present, else to
a bot queue.

## Copilot Surveys

### Creation

We can create a Copilot for the purpose of post-call surveys. This may be done
by adding messages and questions.

### Consent

When we end with a survey, ther are three options we may use to gain consent for
that survey:

- Automatic - implicit: This is generally used in voice calls
- Automatic - explcit: Customer is asked for consent
- Agent-Initiated: Agent asks for consent, and where the customer agrees, they
will be transferred to a survey copilot

### Usage

We need to enable post-call surveys on the workstream.

For agent-initiated surveys, we will also need a queue where the only agent is
the survey bot user.

### Analytics

Survey results may be viewed from Copilot Studio in Analytics -> Sessions
