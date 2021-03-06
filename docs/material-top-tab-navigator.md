---
id: material-top-tab-navigator
title: createMaterialTopTabNavigator
sidebar_label: createMaterialTopTabNavigator
---

A material-design themed tab bar on the top of the screen that lets you switch between different routes by tapping the route or swiping horizontally. Transitions are animated by default. Screen components for each route are mounted immediately.

```js
createMaterialTopTabNavigator(RouteConfigs, TabNavigatorConfig);
```

## RouteConfigs

The route configs object is a mapping from route name to a route config.

## TabNavigatorConfig

* `initialRouteName` - The routeName for the initial tab route when first loading.
* `order` - Array of routeNames which defines the order of the tabs.
* `paths` - Provide a mapping of routeName to path config, which overrides the paths set in the routeConfigs.
* `backBehavior` - Should the back button cause a tab switch to the initial tab? If yes, set to `initialRoute`, otherwise `none`. Defaults to `initialRoute` behavior.
* `swipeEnabled` - Whether to allow swiping between tabs.
* `animationEnabled` - Whether to animate when changing tabs.
* `configureTransition` - a function that, given `currentTransitionProps` and `nextTransitionProps`, returns a configuration object that describes the animation between tabs.
* `initialLayout` - Optional object containing the initial `height` and `width`, can be passed to prevent the one frame delay in [react-native-tab-view](https://github.com/react-native-community/react-native-tab-view#avoid-one-frame-delay) rendering.
* `tabBarComponent` - Optional, override the component to use as the tab bar.
* `tabBarOptions` - An object with the following properties:
  * `activeTintColor` - Label and icon color of the active tab.
  * `inactiveTintColor` - Label and icon color of the inactive tab.
  * `showIcon` - Whether to show icon for tab, default is false.
  * `showLabel` - Whether to show label for tab, default is true.
  * `upperCaseLabel` - Whether to make label uppercase, default is true.
  * `pressColor` - Color for material ripple (Android >= 5.0 only).
  * `pressOpacity` - Opacity for pressed tab (iOS and Android < 5.0 only).
  * `scrollEnabled` - Whether to enable scrollable tabs.
  * `tabStyle` - Style object for the tab.
  * `indicatorStyle` - Style object for the tab indicator (line at the bottom of the tab).
  * `labelStyle` - Style object for the tab label.
  * `iconStyle` - Style object for the tab icon.
  * `style` - Style object for the tab bar.
  * `allowFontScaling` - Whether label font should scale to respect Text Size accessibility settings, default is true.

Example:

```js
tabBarOptions: {
  labelStyle: {
    fontSize: 12,
  },
  tabStyle: {
    width: 100,
  },
  style: {
    backgroundColor: 'blue',
  },
}
```

## `navigationOptions` for screens inside of the navigator

#### `title`

Generic title that can be used as a fallback for `headerTitle` and `tabBarLabel`.

#### `swipeEnabled`

True or false to enable or disable swiping between tabs, if not set then defaults to TabNavigatorConfig option swipeEnabled.

#### `tabBarIcon`

React Element or a function that given `{ focused: boolean, tintColor: string }` returns a React.Node, to display in tab bar.

#### `tabBarLabel`

Title string of a tab displayed in the tab bar or React Element or a function that given `{ focused: boolean, tintColor: string }` returns a React.Node, to display in tab bar. When undefined, scene `title` is used. To hide, see `tabBarOptions.showLabel` in the previous section.

#### `tabBarOnPress`

Callback to handle tap events; the argument is an object containing:

* the `previousScene: { route, index }` which is the scene we are leaving
* the `scene: { route, index }` that was tapped
* the `jumpToIndex` method that can perform the navigation for you

Useful for adding a custom logic before the transition to the next scene (the tapped one) starts.
