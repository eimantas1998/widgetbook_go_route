# Widgetbook

A flutter package that helps cataloguing widgets. Inspired by Storybook.js and flutterbook.

## Let us know how you feel about Widgetbook

We are funded and aim to shape `Widgetbook` to your (and your team's) needs. If you have questions, feature requests or issues let us know on [Discord](https://discord.gg/zT4AMStAJA) or [GitHub](https://github.com/firecrownpro/widgetbook). We're looking forward to build a community and discuss your feedback on our channel! 💙

## Getting Started

This package provides a flutter widget `Widgetbook` in which custom widgets from your app can be injected.

### Enabling Hot Reload

Wrap the `Widgetbook` into a stateless widget to enable hot reloading whenever changes are made to the `Widgetbook`'s parameters. 
```dart
class HotReload extends StatelessWidget {
  const HotReload({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Widgetbook(...);
  }
}
```

### Running the Widgetbook

To run the `Widgetbook` create a new main method, e.g. in `stories/main.dart`:

```dart
void main() {
  runApp(HotReload());
}
```

Run the `Widgetbook` main method by executing `flutter run -t stories/main.dart`.

### Inject your widgets

Your widgets can be organized into different areas of interest by using `Category`, `Folder`, `WidgetElement` and `Story`.

```dart
class HotReload extends StatelessWidget {
  const HotReload({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Widgetbook(
      categories: [
        Category(
          name: 'widgets',
          widgets: [
            WidgetElement(
              name: '$CustomWidget',
              stories: [
                Story(
                  name: 'Default',
                  builder: (context) => CustomWidget(),
                ),
              ],
            ),
          ],
          folders: [
            Folder(
              name: 'Texts',
              widgets: [
                WidgetElement(
                  name: 'Normal Text',
                  stories: [
                    Story(
                      name: 'Default',
                      builder: (context) => Text(
                        'The brown fox ...',
                      ),
                    ),
                  ],
                ),
              ],
            ),
          ],
        ),
      ],
      appInfo: AppInfo(
        name: 'Widgetbook Example',
      ),
    );
  }
}
```

## Set storybook name

Customize `Widgetbook`'s name regarding to the project by using appInfo:

```dart
Widgetbook(
  appInfo: AppInfo(
    name: 'Your apps name',
  ),
)
```

## Adding Themes

Import your app's theme for a realistic preview by using `Widgetbook`'s `lightTheme` and `darkTheme` properties:
```dart
Widgetbook(
  lightTheme: lightTheme,
  darkTheme: darkTheme,
)
```

## Add devices

Customize the preview by defining preview devices: 

```dart
Widgetbook(
  devices: [
    Apple.iPhone11,
    Apple.iPhone12,
    Samsung.s10,
    Samsung.s21ultra,
  ]
)
```

Right now there is a predefinied short list of devices but let us know what you need in your [Discord](https://discord.gg/zT4AMStAJA). We will expand the list of predefinied devices in the future!

# Upcoming features

◼ Search bar

◼ More predefined devices

As already said: Let us know if you need anything! 