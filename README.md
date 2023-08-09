# Toastification  [![pub package](https://img.shields.io/pub/v/toastification?color=blue&style=plastic)](https://pub.dartlang.org/packages/toastification)

Toastification is a Flutter package that allows developers to easily display toast notifications in their apps. Toast notifications are a type of pop-up message that typically appear on the screen and disappear after a short amount of time. They are commonly used to display information, alerts, or confirmations to the user.

One of the advantages of the Toastification package is its ability to handle multiple toast messages. With Toastification, developers can display multiple toast notifications at once and display them in a queue. This means that if multiple notifications are triggered at the same time, they will be displayed one after the other, rather than overlapping on the screen.

Overall, Toastification is a useful package for Flutter developers who want to add toast notifications to their apps without having to write the code from scratch.

## Installation

To use Toastification, you need to add it to your pubspec.yaml file:

``` yaml
dependencies:
  toastification: latest_version
```

Then, run `flutter pub get` to install the package.

## Usage

To use Toastification in your Flutter app, first import the package:

``` dart
import 'package:toastification/toastification.dart';
```

before we dive into the details, you should know that you can use Toastification in two different way:

`toastification.show` Method: to show predefined toast messages with predefined styles.
`toastification.showCustom` Method: to show custom toast messages with custom styles.

you can either use the 'toastification' instance or 'Toastification()' constructor to access the methods.


### Show Method
by using the `show` method, you can show predefined toast messages. you can use the `ToastificationType` enum to choose the type and `ToastificationStyle` enum to choose the style of the toast message.


<p align="center">
<img src="doc\image\types.png?raw=true" width="100%" alt="Riverpod" />
</p>


```dart
toastification.show(
  context: context,
  title: 'Hello, world!',
  autoCloseDuration: const Duration(seconds: 5),
);
```

This will display a toast message with the text "Hello, world!".

You can customize the appearance of the toast message by passing in additional parameters to the `show()` method:

``` dart
toastification.show(
  context: context,
  type: ToastificationType.success,
  style: ToastificationStyle.flat,
  autoCloseDuration: const Duration(seconds: 5),
  title: 'Hello, World!',
  description: 'This is a sample toast message.',
  alignment: Alignment.topRight,
  direction: TextDirection.ltr,
  animationDuration: const Duration(milliseconds: 300),
  animationBuilder: (context, animation, alignment, child) {
    return FadeTransition(
      turns: animation,
      child: child,
    );
  },
  icon: const Icon(Icons.check),
  primaryColor: Colors.green,
  backgroundColor: Colors.white,
  foregroundColor: Colors.black,
  padding: const EdgeInsets.symmetric(horizontal: 12, vertical: 16),
  margin: const EdgeInsets.symmetric(horizontal: 12, vertical: 8),
  borderRadius: BorderRadius.circular(12),
  boxShadow: const [
    BoxShadow(
      color: Color(0x07000000),
      blurRadius: 16,
      offset: Offset(0, 16),
      spreadRadius: 0,
    )
  ],
  onCloseTap: () {
    // Do something when the toast is closed
  },
  showProgressBar: true,
  closeButtonShowType: CloseButtonShowType.onHover,
  closeOnClick: false,
  pauseOnHover: true,
  dragToClose: true,
);
```


### ShowCustom Method

If you are looking for even more control over the appearance and behavior of your toast messages, you can use the showCustom() method to create a completely custom toast message. This method lets you pass in a builder function that returns the widget you want to display, giving you complete control over the toast's layout, styling, and interactivity.

With showCustom(), the possibilities are endless. You can create a custom toast message that matches your app's unique visual style, or you can add interactive elements like buttons and sliders to make your toast messages more engaging and dynamic.

Here's an example of how to use showCustom() to create a custom toast message with a button that lets users perform an action:

```dart
toastification.showCustom(
  context: context,
  autoCloseDuration: const Duration(seconds: 5),
  alignment: Alignment.topRight,
  builder: (BuildContext context, ToastificationItem holder) {
    return Container(
      decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(8),
        color: Colors.blue,
      ),
      padding: const EdgeInsets.all(16),
      margin: const EdgeInsets.all(8),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          const Text('Custom Toast',
              style: TextStyle(
                  color: Colors.white, fontWeight: FontWeight.bold)),
          const SizedBox(height: 8),
          const Text('This is a custom toast message!',
              style: TextStyle(color: Colors.white)),
          const SizedBox(height: 16),
          Row(
            children: [
              ElevatedButton(
                onPressed: () {
                  // Perform an action when the button is pressed
                },
                child: const Text('Do Something'),
              ),
            ],
          ),
        ],
      ),
    );
  },
);
```
With showCustom(), you're only limited by your imagination. Create a toast message that stands out from the crowd and adds a touch of personality to your app!


### Custom Animations

You can customize the animation of the toast notification by providing a Duration for the animation duration and implementing your own animation builder function using the animationBuilder parameter. Here's an example of how to use custom animations:

```dart
toastification.show(
  context: context,
  title: 'Hello, world!',
  // .... Other parameters
  animationDuration: const Duration(milliseconds: 300),
  animationBuilder: (context, animation, alignment, child) {
    return RotationTransition(
      turns: animation,
      child: child,
    );
  },
);
```
### Global/Default Configuration


### Manage Your Notifications

In addition to displaying toast messages, the Toastification package also provides methods for managing and dismissing existing notifications. Here are the available methods:



#### Find a Notification item

Find a notification with the given ID

```dart
final notification = toastification.findToastificationItem('my_notification');
```
#### Dismiss a Notification

Remove a specific notification from the screen.

```dart
final notification = toastification.show(
  context: context,
  title: 'Hello',
  autoCloseDuration: const Duration(seconds: 5),
);

toastification.dismiss(notification);
```

#### Dismiss a Notification by ID

Remove a notification with the given ID from the screen.

``` dart
toastification.dismissById('my_notification_id');
```

#### Dismiss the First Notification

Remove the first notification that was shown from the screen.

```dart
toastification.dismissFirst();
```


#### Dismiss the Last Notification

Remove the last notification that was shown from the screen.

```dart
toastification.dismissLast();
```


## Contributions

Contributions are always welcome! If you have any suggestions, bug reports, or feature requests, please open an issue on the GitHub repository.

If you would like to contribute to the project, please read the [CONTRIBUTING.md](https://github.com/payam-zahedi/toastification/CONTRIBUTING.md "CONTRIBUTING.md") file for more information on how to contribute.


## License

Toastification is released under the `BSD-3-Clause` License. You can find the full text of the license in the LICENSE file in the root of the repository.


#### * Written with the help of Chat GPT
