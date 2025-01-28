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



