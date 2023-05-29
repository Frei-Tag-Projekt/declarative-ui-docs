# Text

#### SwiftUI

```Swift
Text(“Sample Text”)
```

#### Flutter

```Dart
Text(‘Sample Text’);
```

#### Jetpack Compose

```Kotlin
Text(“Sample Text”)
```

# Button

#### SwiftUI

```Swift
Button(“Displayed text”) {
    print(“Button was pressed”)
}
```

#### Flutter

```Dart
TextButton(
  onPressed: () { print(‘Button was pressed’); },
  child: Text(‘Displayed text’),
);

```
[Docs](https://api.flutter.dev/flutter/material/ButtonStyle-class.html#material-3-button-types)

#### Jetpack Compose

```Kotlin
Button(
    onClick = { print(“Button was pressed”) }
) {
    Text(“Displayed Text”)
}
```

# Image

#### SwiftUI
```Swift
Image(“Asset Name”)
```

#### Flutter

```Dart
```

#### Jetpack Compose

```Kotlin
Image(
    painter = painterResource(id = R.drawable.dog),
    contentDescription = stringResource(id = R.string.dog_content_description)
)
```

# Shapes

#### SwiftUI

```Swift
Rectangle()

Circle()

```

# TextField

#### SwiftUI

```Swift

@State var enteredText = “Default Text”

TextField($enteredText)

```

# Sheet

#### SwiftUI

```Swift
@State var isSheetPresented = false

Button(“Present Sheet”) {
  isSheetPresented = true
}.sheet(isPresented: $isSheetPresented) {
  Text(“Sheet is presented”)
}
```
