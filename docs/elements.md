---
title: Elements
---
# Elements 

Everyone of the frameworks has similar basic building blocks

## Text

Text is really powerful in every framework, it is also one of the simplest building blocks. It displays the string that is passed to it.

#### SwiftUI

```Swift
Text(“Sample Text”)
```

[Docs](https://developer.apple.com/documentation/swiftui/text)

#### Flutter

```Dart
Text(‘Sample Text’);
```

[Docs](https://api.flutter.dev/flutter/widgets/Text-class.html)

#### Jetpack Compose

```Kotlin
Text(“Sample Text”)
```

[Docs](https://developer.android.com/jetpack/compose/text)

## Button

#### SwiftUI

```Swift
Button(“Displayed text”) {
    print(“Button was pressed”)
}
```

[Docs](https://developer.apple.com/documentation/swiftui/button)

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

[Docs](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#button)

## Image

#### SwiftUI
```Swift
Image(“AssetName”)
```

[Docs](https://developer.apple.com/documentation/swiftui/image)

#### Flutter

```Dart
Image.asset(’pathTo/AssetName.png‘)
```

[Docs](https://api.flutter.dev/flutter/widgets/Image/Image.asset.html)

#### Jetpack Compose

```Kotlin
Image(
    painter = painterResource(id = R.drawable.dog),
    contentDescription = stringResource(id = R.string.dog_content_description)
)
```

[Docs](https://api.flutter.dev/flutter/widgets/Image/Image.asset.html)

## Shapes

#### SwiftUI

```Swift
Rectangle()
    .fill(Color.red)
    .frame(width: 100, height: 100)

Circle()
    .fill(Color.red)
    .frame(width: 100, height: 100)
    
```
[Docs](https://developer.apple.com/documentation/swiftui/shape)

#### Flutter
```Dart

```

#### Jetpack Compose

```Kotlin
Box(
    modifier = Modifier.size(100.dp).clip(RectangleShape).background(Color.Red)
)

Box(
    modifier = Modifier.size(100.dp).clip(CircleShape).background(Color.Red)
)
```

## TextField

#### SwiftUI

```Swift
struct SimpleTextField: View {
    @State var enteredText = “Default Text”
    
    var body: some View {
        TextField($enteredText)
    }
}
```

#### Jetpack Compose

```Kotlin
@Composable
fun SimpleTextField() {
    var enteredText by remember { mutableStateOf(TextFieldValue("Default Text")) }

    TextField(
        value = text,
        onValueChange = { newText ->
            enteredText = newText
        }
    )
}
```

[Docs](https://developer.android.com/jetpack/compose/text#enter-modify-text)

## Sheet

#### SwiftUI

```Swift
@State var isSheetPresented = false

Button(“Present Sheet”) {
  isSheetPresented = true
}.sheet(isPresented: $isSheetPresented) {
  Text(“Sheet is presented”)
}
```

#### Jetpack Compose

```Kotlin
ModalBottomSheet(onDismissRequest = { /* Executed when the sheet is dismissed */ }) {
    Text(”Sheet is presented”)
}
```

[Docs](https://developer.android.com/jetpack/compose/layouts/material#bottom-sheets)
