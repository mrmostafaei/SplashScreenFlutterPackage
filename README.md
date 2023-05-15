# [MiladTech Splash Screen](https://pub.dev/packages/miladtech_splashscreen)
 
* A splashscreen package to be used for an intro for any flutter application easily with a lot of customization

## Currently Supported by awesome [MiladTech](https://milad-tech.com)


* [MiladTech](https://milad-tech.com) is a new generation of cloud platforms and aims to help developers in their road with open source contributions, and at the end we can say thanks.


## Usage

[Example](https://github.com/mrmostafaei/SplashScreenFlutterPackage/blob/master/example/example.dart)

To use this package :

* add the dependency to your [pubspec.yaml](https://github.com/mrmostafaei/SplashScreenFlutterPackage/blob/master/pubspec.yaml) file.

```yaml
  dependencies:
    flutter:
      sdk: flutter
    miladtech_splashscreen:
```

### How to use

``` dart
new SplashScreen.timer(
  seconds: 14,
  navigateAfterSeconds: new AfterSplash(),
  title: new Text('Welcome In SplashScreen'),
  image: new Image.asset('screenshot.png'),
  backgroundColor: Colors.white,
  styleTextUnderTheLoader: new TextStyle(),
  photoSize: 100.0,
  loaderColor: Colors.red
);
```

## Example

As time based...

``` dart
import 'package:flutter/material.dart';
import 'package:miladtech_splashscreen/splashscreen.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SplashScreen.timer(
      seconds: 14,
      navigateAfterSeconds: AfterSplash(),
      title: Text(
        'Welcome In SplashScreen',
        style: TextStyle(fontWeight: FontWeight.bold, fontSize: 20.0),
      ),
      image: Image.network(
        'https://flutter.io/images/catalog-widget-placeholder.png',
      ),
      backgroundColor: Colors.white,
      loaderColor: Colors.red,
    );
  }
}

class AfterSplash extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Welcome In SplashScreen Package'),
        automaticallyImplyLeading: false,
      ),
      body: Center(
        child: Text(
          'Succeeded!',
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 30.0),
        ),
      ),
    );
  }
}
```

As future based...

``` dart
import 'package:flutter/material.dart';
import 'package:miladtech_splashscreen/splashscreen.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

Future<Widget> loadFromFuture() async {
  // <fetch data from server. ex. login>
  return AfterSplash();
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SplashScreen.future(
      navigateAfterFuture: loadFromFuture(),
      navigateAfterSeconds: AfterSplash(),
      title: Text(
        'Welcome In SplashScreen',
        style: TextStyle(fontWeight: FontWeight.bold, fontSize: 20.0),
      ),
      image: Image.network(
        'https://flutter.io/images/catalog-widget-placeholder.png',
      ),
      backgroundColor: Colors.white,
      loaderColor: Colors.red,
    );
  }
}

class AfterSplash extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Welcome In SplashScreen Package'),
        automaticallyImplyLeading: false,
      ),
      body: Center(
        child: Text(
          'Succeeded!',
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 30.0),
        ),
      ),
    );
  }
}
```

### Animate the main image with the hero animation

The main image has this tag attached to it `splashscreenImage`. Add it to whatever page you'll navigate to. This will animate the main Image to the same image you put in another page

### Adding a custom page tranistion

You can use the `pageRoute` to do just this. Here's an example

```dart
import 'package:flutter/material.dart';
import 'package:miladtech_splashscreen/splashscreen.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

Route _createRoute() {
  return PageRouteBuilder(
    pageBuilder: (context, animation, secondaryAnimation) => AfterSplash(),
    transitionsBuilder: (context, animation, secondaryAnimation, child) {
      var begin = Offset(0.0, 1.0);
      var end = Offset.zero;
      var curve = Curves.ease;
      var tween = Tween(begin: begin, end: end).chain(CurveTween(curve: curve));
      return SlideTransition(
        position: animation.drive(tween),
        child: child,
      );
    },
  );
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SplashScreen.timer(
      seconds: 14,
      navigateAfterSeconds: AfterSplash(),
      title: Text(
        'Welcome In SplashScreen',
        style: TextStyle(fontWeight: FontWeight.bold, fontSize: 20.0),
      ),
      image: Image.network(
        'https://flutter.io/images/catalog-widget-placeholder.png',
      ),
      backgroundColor: Colors.white,
      loaderColor: Colors.red,
      pageRoute: _createRoute(),
    );
  }
}

class AfterSplash extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Welcome In SplashScreen Package'),
        automaticallyImplyLeading: false,
      ),
      body: Center(
        child: Text(
          'Succeeded!',
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 30.0),
        ),
      ),
    );
  }
}
```
### About MiladTech

[MiladTech](https://milad-tech.com) is a SaaS tool that helps developers just like you to deploy their web apps more easily.

### Created by [MiladTech](https://github.com/mrmostafaei)
