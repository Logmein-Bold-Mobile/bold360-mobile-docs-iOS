> This article will help you customize initial chat view UI, and instruct you how to change UI on runtime according to live data.

## Customizing UI components 

In order to change and override provided SDK implementations and customizations, one need to provide his own changed `ChatConfiguration` instance on `ChatController.viewConfiguration`. 

### Supported Configurations


| Configuration Class Name     | Configuration Options                                                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `ChatViewConfiguration`      | backgroundColor, backgroundImage, dateStampColor, customFont                                                                        |
| `IncomingBotConfiguration`   | quickOptionConfig, persistentOptionConfig                                                                                           |
| `IncomingLiveConfiguration`  | backgroundColor, backgroundImage, dateStampColor, customFont, avatar, textColor                                                     |
| `OutgoingConfiguration`      | backgroundColor, backgroundImage, dateStampColor, customFont, avatar, textColor, sentSuccessfullyIcon, sentFailureIcon, pendingIcon |
| `CarouselConfiguration`      | backgroundColor, backgroundImage, dateStampColor, customFont, avatar, textColor                                                     |
| `SystemMessageConfiguration` | backgroundColor, backgroundImage, dateStampColor, customFont, avatar, textColor    


### Hot To Set Configuration

In following sample we will customize chat view.

```swift
self.chatController.viewConfiguration.chatViewConfig.backgroundImage = UIImage(named: "ww_back_light")
self.chatController.viewConfiguration.chatViewConfig.dateStampColor = UIColor.black
```

### Set Custom Font

To set custom font first make sure to add the relevant file to project, then:

```swift
// For example our custom font is: `{CUSTOM_FONT_NAME}.ttf`
let font = CustomFont()
font.fontFileName = "{CUSTOM_FONT_NAME}.ttf"
font.font = UIFont(name: "{CUSTOM_FONT_NAME}", size: 15)
let font1 = CustomFont()
font1.fontFileName = "{CUSTOM_FONT_NAME}.otf"
font1.font = UIFont(name: "{CUSTOM_FONT_NAME}", size: 20)
self.chatController.viewConfiguration.outgoingConfig.customFont = font
self.chatController.viewConfiguration.incomingBotConfig.customFont = font1
self.chatController.viewConfiguration.incomingLiveConfig.customFont = font

```

## Avatar Positioning 

`ChatElementConfiguration` has a property `avatarPosition` of type `AvatarPosition` the default value for outgoing element is `AvatarPositionBottomLeft` and for incoming element is `AvatarPositionBottomRight` for changing the position:

```swift
self.chatController.viewConfiguration.incomingBotConfig.avatarPosition = .topLeft
```

### Avatar Position Options

``` Objective C
typedef NS_ENUM(NSInteger, AvatarPosition) {
    AvatarPositionTopLeft,
    AvatarPositionBottomLeft,
    AvatarPositionTopRight,
    AvatarPositionBottomRight
};
```
