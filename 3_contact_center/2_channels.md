# Accounts and Channels

## General

## Chat Channels

We can deploy a live chat widget using a chat channel. This functionality allows
us to:

- Customise theming and branding
- Use pre and post chat surveys
- Get user details from authenticated and non-authenticated users
- Configure file transfer permissions and chat transcripts
- Enable Proactive chat
- Convigure voice and video call support

### Requirements
- A subscription to the D365 Messaging Service
- A licence for each agent using chat

### Chat Widget Behaviors

We can configure various behaviours for the widget:

#### Custom automated messages

Here we can define custom messages to be sent based on predefined triggers, e.g. 
when out of operating hours

##### Customer Wait Time

This is a separate option, but does the same thing. We can enable automated
messages to show queue position and average wait time. These are simple booleans
so we do not need to define the trigger or message content.

#### Pre-conversation surveys

We can define a set of simple questions to ask customers. The answers may be:
- single line text 
- multi-line text 
- option set
- user consent

We can also specify if each is required

When designing these note that the system will try and search for accounts, 
contacts and cases. It will look at:
- Accounts and contacts: Name, email and phone number
- Cases: Case number field

We can design our questions to help this search.

#### Post-conversation surveys

Here we can connect a Customer Voice survey to be sent after the conversation.
This may be inserted within the widget or sent as a link in the widget.

We can also indicate wheter surveys should be sent for conversations which were
handled excusively by a bot.

#### Authentification Settings

We can require that a user is authenticated before starting a chat. This can
be a good way of getting details about a customer. However, we need to define
an authentication setting, for live chat we can use OAuth 2.0.

#### Location Detection

When this is turned on customer will be prompted to allow location detection

### user Features

We can define various user features:

- Allow file attachments for users and agents
- Send users notifications for messages
- Allow download/email of conversation transcripts
- Allow agents to switch to voice and/or video calls during a chat session
- Allow Screen sharing
- Allow co-browse

### Proactive Chat

This enables messages to be sent to users based on preconfigured rules. Triggers
may include time spent on a page, pages visited etc.

We first need to enable proactive chat.

```js
<script id="Proactivechattrigger">

    window.addEventListener("lcw:ready", function handleLivechatReadyEvent(){
		var timeToWaitBeforeOfferingProactiveChatInMilliseconds = 20000;
        Microsoft.Omnichannel.LiveChatWidget.SDK.setContextProvider(
            function contextProvider(){
            return {
                'Proactive Chat':{'value':'True','isDisplayable':true},
                'Time On Page':{
                    'value': timeToWaitBeforeOfferingProactiveChatInMilliseconds,
                    'isDisplayable':true
                    },
                'Page URL':
                {'value': window.location.href, 
                'isDisplayable':true
                },
            };
        });
		
		//Display proactive chat invite after 'timeToWaitBeforeOfferingProactiveChatInMilliseconds' milliseconds
        setTimeout(function(){
            Microsoft.Omnichannel.LiveChatWidget.SDK.startProactiveChat(
                {message: "Hi! Just checking in to see if I can help answer any questions you may have."},
                 false)
        }
        ,timeToWaitBeforeOfferingProactiveChatInMilliseconds);
    });
</script>
```

Where this is set-up:

If the customer accepts the invitation, the context details will be displayed in
the additional details tab of the conversation summary. This includes:
- Time on page
- Page URL

As can be seen from the script, we set a timeout on a page after which we call
the startProactiveChatMethod.

We also define a context provide which is used to provide context values for the
page: Here, time on page and the page URL.

I think the context values and their types are defined in the workstream.


## Deploy a Chat Widget in a Portal

In our own sites we can simply copy the code. In a model driven application
we need to add a content snippet. If we have multiple widgets we can use 
conditional rules in our snippet, e.g.:

```html
{%if user%}
    <script ... />
{%else%}
    <script ... />
{%endif%}
```
## Voice Channel

### Requirements

We need to:
- Provision the voice channel (omnichannel installation config)
- Ensure that the correct licencing is in place

### Manage Phone Numbers

Omnicahnnel uses Azure Communication Services for calling and text capabilities.
We will need to purchas a phone number and call plan to use this service.

Phone numbers are added from the Accounts section in Admin Center -> Channels

When adding the first phone number. A resource needs to be created which 
specifies:
- The subscription to use
- The resource group where Azure Communication Service resources will be stored

For subsequent numbers we do not need to specify these details. 

We then specify the number type:
- Toll Free (sms and voice)
- Geographic (voice only)

Depending on the number type:

- specify area code/geographic location
- optionally, enable receive and/or make calls
- optionally, enable send or send and receive sms

Also specify area code/geographic location for toll free and geographic types 
respectively.

It is possible to edit and release phone numbers, however, the number must
first be removed from the workstream it is attached to.

### Overflow Handling

The queue may receive too many incoming calls at once. We can set up overflow
handling rules in the queue to help manage this.

### Voice Channels

We can define a voice channel, as with chat we can specify various behaviours
specific to this channel, such as:

- Customer wait time: Notifications about position in queu and average wait time
- Channel operating hours
- Transcription and recording options
- Custom automated messages
- Enable call transfer to external agents
- Consults with team users

We can also define voice profiles used of voice bots and automated messages.

### Voice Workstream

It is difficult to find information here, but it looks like a workstream can
only be associated with one phone number.

It is certainly the case that a phone number may only be associated with a 
single workstream.

### Voice Queues

The default assignment method in the default voice queue is apparantly 
round robin.

However, in the trial, the default voice assignment options are:
- Highest capacity
- Advance round robin
- Least active (default)

## SMS Channel

The first thing to note, is like all channels sms has some peculiarities:

- The maximum chars for text messages is 1,600
- Customer Service will try to match an incoming message to an account based on
the mobile phone field in the customer record

### Requirements
- SMS functionality must be enabled in the environment (omnichannel set-up)
- An account and SMS number must be registered. The supported providers are:
    - Azure Communication Services
    - Twilio or Telesign account

The last screen of the account set-up has a callback url. If using Twilio we
need to add this url in our Twilio account for the phone number. 

### Channels

This is all very similar to other channels. We can set-up behaviours for the 
channel:

- Operating hours
- Custom automated messages
- Post-conversation surveys

We can also set-up user features:
- Customers can send file attachments
- Agents can send file attachments

### Workstreams

This is fairly standard, but there is an additional option in the work
distribution section:

- Auto-close after inactivity: Default is 2 days before a conversation is closed

## Social Channels

### Requirements

- The channel must be enabled (Omnichannel set-up)
- Customer Service Digital Messaging Add-On licence is required

### Supported Channels

- Facebook
- LINE
- Twitter/X
- WhatsApp
- WeChat

### Accounts

#### Facebook

We need a:
- Facebook page with Messenger enables
- Facebook application
- To add CS webhooks to the Facebook Appolication

On the Customer Service side we need an App Id and App secret.

Note, if attachments are not disabled, this will not prevent the user from 
sending attachments, it will just prevent agents from receiving the file and an
error will be thrown.

#### LINE

To set up a line account we need:

- LINE handle and a LINE channel in the LINE developer console
- Configure the CS webhook with the callback uri and verification token

On the Customer Service side we need a Channel Id, secret and access token

#### WhatsApp

We need to integrate WhatsApp using Twilio. We will need:

- A Twilio account, with a number connected to a WhatsApp business profile
- The callback url should be added to the Twilio inbound url box

On the Customer Service side, we will need the Account SID and auth token.

### Channel Set-Up

This is all standard.

### WhatsApp Peculiarities

Beyond integration through Twilio there are additional peculiarities with 
WhatsApp:

#### 24 Hour Rule
 
Agents may send messages to customers within 24 hours of a message being 
received. It appears that the time is reset everytime a new message is received.

Messages sent in this timeframe are termed session messages.

Outside of the session, agents may only send template messages. These are 
messages send using preapproved templates. The user must also opt in to 
receiving messages from the organisation.

## Google Business Messages and Apple Message for Business 

### Channels

#### Google Business Messages

- Register as a partner with Google messages
- Create a sevice account to authenticate API calls
- Set up an agent accociated with the channel
- Add the CS webhook to the google account 

#### Apple Messages for Business Account

- Create an Apple messages for business account
- Configure the callback url

On the Customer Service side, 

### Apple Messages for Business Additional Features

We can take advantage of a number of additional features when using an Apple
Messages for Business account:

#### Rich Messages

We can use rich messages, these allow us to use interactive content, such as
providing a user with a list of options they may select from.

This can be particularly useful when used in conjunction with Apple Pay as we
can capture details necessary to process payments.

Rich messages may be created from Admin Center -> Productivity -> Rich Messages

These messages are channel specific.

As with quick replies, we can define tags to help agents find these messages.

The types of messages include:
- Apple Pay
- Authorisation
- Forms
- List Picker
- Suggested respectively
- Time Picker
- Video rich link
- Website Rich link
- Custom JSON

The designer mode used to create the message will depend on the type chosen.

By default, rich messages are available throughout the org. If we associate a 
message with one or more workstreams it will be limited to these.

#### Apple Pay

To use apple pay we need to define payment profiles. These contain the 
information required to connect to the relevant Apple merchant store.

Once created, we can add the payment profile to a channel.

We can associate a rich message with a payment profile.






























