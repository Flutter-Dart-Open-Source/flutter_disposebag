# flutter_disposebag

## Author: [Petrus Nguyễn Thái Học](https://github.com/hoc081098)

[![Pub](https://img.shields.io/pub/v/flutter_disposebag)](https://pub.dev/packages/flutter_disposebag)
[![Pub Version](https://img.shields.io/pub/v/flutter_disposebag?include_prereleases)](https://pub.dev/packages/flutter_disposebag)
[![codecov](https://codecov.io/gh/Flutter-Dart-Open-Source/flutter_disposebag/branch/master/graph/badge.svg?token=g0vMFL9L2Q)](https://codecov.io/gh/Flutter-Dart-Open-Source/flutter_disposebag)
[![Flutter Tests](https://github.com/Flutter-Dart-Open-Source/flutter_disposebag/workflows/Flutter%20Tests/badge.svg)](https://github.com/Flutter-Dart-Open-Source/flutter_disposebag.git)

*   A package to help disposing Streams and closing Sinks easily for Flutter.
*   Automatically disposes `StreamSubscription` and closes `Sink` when disposing `State<T>`.

## Medium article

[How to easily cancel streams in Flutter](https://hoc081098.medium.com/how-to-easily-cancel-streams-in-dart-flutter-69cad1980267)

## Usage

A simple usage example:

```dart
import 'dart:async';

import 'package:flutter/material.dart';
import 'package:flutter_disposebag/flutter_disposebag.dart';

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> with DisposeBagMixin {
  final controller = StreamController<int>();

  @override
  void initState() {
    super.initState();

    Stream.periodic(const Duration(milliseconds: 500), (i) => i)
        .listen((event) {})
        .disposedBy(bag);

    controller.stream.listen((event) {}).disposedBy(bag);
    controller.disposedBy(bag);
  }

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```

## Features and bugs

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: https://github.com/hoc081098/disposebag/issues/new
