---
layout: default
title: Events and Notifications
parent: Tracking Events
grand_parent: Chat Configuration
nav_order: 3
# permalink: /docs/chat-configuration/tracking-events/events-and-notifications
---

# Events and Notifications
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## Listening to chat elements changes

In order to be able to be notified of all elements changes in the chat, implement `ChatElementDelegate`, and register as follows:

```swift
controller.chatElementDelegate = self
```

### Possible updates 

`didReceive`(req) - on element inserted to the chat.   

`remove`(opt) - element was removed from the chat.   

`didUpdateChatElement`(opt) - element data was updated.

`didUpdateFeedback`(opt) - element feedback was updated.

`fetch`(opt) - implement this in order to enable display of previous chat content. (Historic content)

```swift
 func didReceive(_ item: StorableChatElement!) {
    //use item     
}
```