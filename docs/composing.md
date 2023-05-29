# Composing Views

The goal of all these UI-frameworks is to structure the app in small reusable pieces that are easy to maintain and understand. Every langauge has it’s own way of defining such a piece. In SwiftUI everything is a view, in Flutter everything is a widget and in Jetpack Compose everything is a composable function

## Overview

* [Structure UI in components](./composing.md#components)
* [Parameterise components](./composing.md#components)
* [Default value for components](./composing.md#components)
* [Passing actions](./composing.md#components)
* [Wrapping views](./composing.md#components)

## Components

#### SwiftUI

```Swift
struct SampleView: View {
  var body: some View {
    // Parts of the view
  }
}

// Using this view as part of another view
SampleView()
```
[Docs](https://developer.apple.com/documentation/swiftui/view)
#### Flutter

```Dart
class SampleView extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return // Parts of the view
  }
}

// Using this view as part of another view
SampleView();
```

#### Jetpack Compose

```Kotlin
@Composable
fun SampleView() {
    // Parts of the view
}

// Using this view as part of another view
SampleView()
```
[Docs](https://developer.android.com/jetpack/compose/mental-model)

## Passing data into a view

Passing data allows to paramterize each component

#### SwiftUI

```Swift
struct SampleView: View {
  let title: String

  var body: some View {
    Text(title)
  }
}

// Using this view as part of another view
SampleView(title: „Sample“)
```
[Docs](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/initialization/)

#### Flutter

```Dart
class SampleView extends StatelessWidget {

  final String title;
  
  SampleView({
      required this.title
  })

  @override
  Widget build(BuildContext context) {
    return Text(title);
  }
}

// Using this view as part of another view
SampleView(‚Sample‘);
```

#### Jetpack Compose

```Kotlin
@Composable
fun SampleView(title: String) {
    Text(title)
}

// Using this view as part of another view
SampleView(“Sample“)
```

## Default Values

#### SwiftUI

```Swift
struct SampleView {

  var title = “Default Title”

  var body: some View {
    Text(title)
  }
}

// title is “Default Title”
SampleView()

// title is “Other Title”
SampleView(title: “Other Title”)
```
[Docs](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/initialization/)

#### Flutter

```Dart
class SampleView extends StatelessWidget {

  final String title;
  
  SampleView({
      this.title = ‘Default Title’
  })

  @override
  Widget build(BuildContext context) {
    return Text(title);
  }
}

// title is ‘Default Title’
SampleView();

// title is ‘Other Title’
SampleView(‘Other Title‘);
```

#### Jetpack Compose

```Kotlin
@Composable
fun SampleView(title: String = “Default Title”) {
    Text(title)
}

// Using this view as part of another view
SampleView(“Sample“)
```
[Docs](https://kotlinlang.org/docs/functions.html)

## Passing Actions

#### SwiftUI

```Swift
struct SampleButton: View {

  let action: () -> Void
  
  var body: some View {
    Button(“Sample”) {
      action()
    }
  }
}

SampleButton {
  print(“SampleButton pressed”)
}

SampleButton(action: { print(“SampleButton pressed”) }
```

```Swift
struct ReturnDateButton: View {

  let action: (Date) -> Void
  
  var body: some View {
    Button(“Return Date”) {
      action(Date.now)
    }
  }
}

ReturnDateButton { returnedDate in
  print(returnedDate)
}
```

```Swift
struct PassDateButton: View {

  let getDate: () -> Date
  
  var body: some View {
    Button(“Get Date”) {
      print(getDate())
    } 
  }
}

PassDateButton {
  return Date.now
}
```

#### Flutter

```Dart

```

#### Jetpack Compose

```Kotlin

```

## Wrapping Components

#### SwiftUI

```Swift
struct ConsoleButton<Label: View>: View {

  var label: () -> Label

  var body: some View {
    Button {
      print(“Button pressed”)
    } label: {
      label()
    }
  }
}
```

#### Flutter

```Dart

```

#### Jetpack Compose

```Kotlin

```