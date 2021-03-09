---
layout: default
title: Agent Typing Indication
parent: UI Customization
grand_parent: Chat Configuration 
# permalink: /docs/chat-configuration/ui-customization/agent_typing_indication/
nav_order: 8
---

# Agent Typing Indication {{site.data.vars.need-work}}
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## Overview
Appears when the live agent is typing.  
The typing indication can be displayed as text and/or drawable.   
Typing drawable can be an [AnimatedVector](https://developer.android.com/reference/android/graphics/drawable/AnimatedVectorDrawable).
{: .overview}

## How to enable
By default typing indication is `enabled`.   
The component display can be disabled through `ConversationSettings`.
```kotlin 
val settings =  ConversationSettings()...
        .disableTypingIndication()

ChatController.Builder(context).apply {
    conversationSettings(settings)
    ...
}
```

## Listening to typing notifications

In order to receive typing state changes, subscribe to `OperatorEvent.OperatorTyping' notifications, with the chatController.
```kotlin
// 1. implement Notifiable interface
// 2. pass the implementation and the list of notifications that you want to receive.  
chatController.subscribeNotifications(NotifiableImpl, OperatorEvent.OperatorTyping,...)
```

> Follow for more info about [notifications subscription]({{'/docs/chat-configuration/tracking-events/events-and-notifications' | relative_url}})

---

## How to customize

Typing indication UI component is provided by the SDK, and can be customize either by configuration setting or by view implementation overriding.

### Customizing by Configure
    Override `ChatUIProvider.typingUIProvider.configure` method:
    ```kotlin
    ChatUIProvider(context).apply {
        typingUIProvider.configure = { adapter:TypingUIAdapter -> 
            ...
        }
    }
    ```
    
### Customizing by override
   Override overrideFactory value with your own `TypingFactory` implementation:
    ```kotlin
    ChatUIProvider(context).apply {
        typingUIProvider.overrideFactory = MyTypingFactory()
    }

    // for e.g.
    class MyTypingFactory : TypingFactory{
        // TypingUIAdapter interface should be 
        // implemented by the overriding component
        return object : TypingUIAdapter{
            ...
        }
    }

    ```
