---
layout: default
title: In chat
parent: Autocomplete
grand_parent: Advanced Topics
nav_order: 1
# permalink: /docs/advanced-topics/autocomplete/in-chat
---

# Autocomplete in AI chat
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc .nb-0}
- [UI configurations]({{'/docs/chat-configuration/ui-customization/user-input-field#ui-configurations' | relative_url}})

---

## Overview
Autocomplete is supported for AI chats only.   
While the user is typing a query, he will be presented with a list of relevant suggested queries, according to the typed content.  Selection of an autocomplete suggestion, will automaticaly send the selection as user query.  
{: .overview}
 
![]({{'/assets/images/autocomplete-in-chat.png' | relative_url}})   
{: .image-40}

---

## Aavailability configuration
{: .mb-4}
- ### [Admin console configuration]({{'/docs/advanced-topics/autocomplete#control-availability' | relative_url}})
{: mb-10}

- ### Chat ConversationSettings configuration   
  Feature availability can be configured by the hosting App, by passing [`ConversationSettings`]({{'/docs/chat-configuration/chat-settings' | relative_url}}) instance, configured with the autocomplete feature desired status, on [`ChatController`]({{'/docs/chat-configuration/extra/chatcontroller' | relative_url}}) creation. The configured availability status will apply on all chats that are created by the same ChatController instance. 
  
    ```kotlin
    val settings = ConversationSettings().apply {
        // ...
        enableAutocompleteSupport(true/false)
    }

    val chatController = ChatController.Builder(context)  
                            .conversationSettings(settings)                                                   
                            .build(account, ...)                    
    ``` 
{: .mb-8}


> **Generally, client side settings will override console settings.**     
    Except for the case were autocomplete was enabled on the App side, but disabled on the admin console, on the account settings, though the autocomplete is enabled and passes requests, no suggestions will be received by the BE nor displayed in the chat.   
{: .mb-10}