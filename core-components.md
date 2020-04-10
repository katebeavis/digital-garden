# Core components

React Native also includes a set of essential, ready-to-use Native Components you can use to start building your app today. These are React Native's Core Components.

## SafeAreaView

`SafeAreaView` renders content with the safe area boundaries of a device. It only works on iOS devices running iOS version 11 or later.

`SafeAreaView` renders nested content and automatically applies padding to reflect the protion of the view that is not covered by nav bars, tab bars, toolbars and other ancestor views.

Most importantly, its paddings reflect the physical limitations of the screen, such as rounded corners or camera notches.

# ScrollView

Wraps platform ScrollView while providing integration with touch locking 'responder' system.

`ScrollView` adds scolling capabitily when wrapping a view.

# View

The most fundamental component when building a UI. `View` is a container that supports layout with flexbox, style, some touch handling and accessibility controls.

`View` is designed to be nested inside other view and can have none or many children.

Maps to `div` in web.

# Text

Displays text. Supports nesting, styling and touch handling.

# TextInput

Allows users to input text via a keyboard. Props can be used to configure several features such as auto-correction, auto-capitalisation, placeholder text and different keyboard types such as a numeric keypad.

# Button

A basic button component that supports some customisation.

You can build your own button using TouchableOpacity or TouchableNativeFeedback.

# ActivityIndicator

Displays a circular loading indicator.

# RefreshControl

Used inside a `ScrollView` or `ListView` to add pull tp refresh functionality. When the `ScrollView` is at `scrollY: 0`, swiping down triggers an `onRefresh` event.

# Picker

Renders the native picker component - picking an option from a list.

# FlatList

A performant interface for rendering basic flat lists.

# SectionList

A performant interface for rendering sectioned lists, supoorting list headers, list footers, item seperators, section headers and section seperators.

#StatusBar

Component to control the app status bar.

#Switch

A switch that is rendered as a boolean input.

#TouchableHighlight

A wrapper for making views respond properly to touches. On press down, the opacity of the wrapped view is decreased, which allows the underlay colour to show though, darkening or tinting the view.

#TouchableOpacity

A wrapper for making views respond properly to touches. On press down, the opacity of the wrapped view is decreased, dimming it.
