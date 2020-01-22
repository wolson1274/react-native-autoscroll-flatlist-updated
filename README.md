# react-native-autoscroll-flatlist

[![react-native-autoscroll-flatlist is released under the MIT license.](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/RageBill/react-native-autoscroll-flatlist/blob/master/LICENSE)
[![build status for react-native-autoscroll-flatlist](https://travis-ci.org/RageBill/react-native-autoscroll-flatlist.svg?branch=master)](https://travis-ci.org/RageBill/react-native-autoscroll-flatlist)

An enhanced version of the original react-native `<FlatList>` component with built-in support for both Javascript and Typescript usage.

This component enables auto-scrolling on new item added to the list - which works like any chat client.

Now supports horizontal `<FlatList>` as well in version `>= 1.6.0`.

# Demo

![demo](https://github.com/RageBill/react-native-autoscroll-flatlist/blob/master/demo/autoscroll.gif?raw=true)

# Features

Auto-scroll is disabled when scrolled away from end of list. There are 3 ways to re-enable auto-scrolling:

- You can manually scroll back to the end of list.

![scroll to end manually](https://github.com/RageBill/react-native-autoscroll-flatlist/blob/master/demo/selfScrollToEnd.gif?raw=true)

- You can tap on the `scrollToEndIndicator` (customizable) shown on the bottom right of the list.

![scroll to end by tapping on scrollToEndIndicator](https://github.com/RageBill/react-native-autoscroll-flatlist/blob/master/demo/scrollToEndIndicator.gif?raw=true)

- You can tap on the `newMessageAlertComponent` (customizable) shown on the top of the list.

![scroll to end by tapping on newMessageAlert](https://github.com/RageBill/react-native-autoscroll-flatlist/blob/master/demo/newMessageAlert.gif?raw=true)

# Installation

```
npm install --save react-native-autoscroll-flatlist
```

or

```
yarn add react-native-autoscroll-flatlist
```

# Example Usage

Import the component with:

```
import AutoScrollFlatList from "react-native-autoscroll-flatlist";
```

and simply use it like an ordinary `<FlatList>`, for example:

```
<AutoScrollFlatList
    ref={this.myRef}
    threshold={20}
    data={myData}
    renderItem={({item, index}) => <YourComponent item={item} index={index} />}
    keyExtractor={item => item.id}
/>
```

You can check out the `example` folder for further details.

# Properties

This component extends the official [`FlatListProps`](https://facebook.github.io/react-native/docs/flatlist) with the following additional props:

| Prop                     | Type                                                                                                         | Required | Default value | Description                                                                       |
| ------------------------ | ------------------------------------------------------------------------------------------------------------ | -------- | ------------- | --------------------------------------------------------------------------------- |
| threshold                | number                                                                                                       | No       | 0             | Distance from end of list to enable auto-scrolling.                               |
| showScrollToEndIndicator | boolean                                                                                                      | No       | true          | Whether to show an indicator to scroll to end.                                    |
| showNewMessageAlert      | boolean                                                                                                      | No       | true          | Whether to show new message alert when auto-scrolling is temporarily disabled.    |
| newMessageAlertRenderer  | (newMessageCount: number, translateY: Animated.Value) => React.ComponentType<any> &#124; React.ReactElement | No       | true          | The component that indicates number of new messages. Best with position absolute. |
| indicatorContainerStyle  | StyleProp<ViewStyle>                                                                                         | No       | see code      | The style for container of the indicator. Best with position absolute.            |
| indicatorComponent       | React.ComponentType<any> &#124; React.ReactElement &#124; null                                               | No       | see code      | The indicator itself. There is a default provided. See code for details.          |
