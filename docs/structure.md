# Structuring views

In this part you will see the comparison how different components are structured regarding size and placement

## Overview:
* [Placement](./Structure.md#placement-of-views)
    * [Components next to each other](./Structure.md#components-next-to-each-other)
    * [Overlapping Components](./Structure.md#overlapping-components)

## Placement of views

How do we place elements on our screen? At first we should think about are they more horizontal placed to each other, vertically or do they overlap.

### Components next to each other

Are the elements next to each other in a row or are they following from the top of the screen to the bottom

#### SwiftUI

```Swift
// VStack is the short for vertical stack. So all these elements are placed from top to bottom
VStack {
  Text(“Top Text”)
  Text(“Middle Text”)
  Text(“Bottom Text”)
}

// HStack is the short for horizontal stack. The elements are placed in the main reading direction. Depending on the language from left to right or right to left
HStack {
  Text(“Leading Text”)
  Text(“Middle Text”)
  Text(“Trailing Text”)
}
```

#### Flutter

```Dart
Column(
  children: [
    Text(‘Top Text’),
    Text(‘Middle Text’),
    Text(‘Bottom Text’),
  ],
);

Row(
  children: [
    Text(‘Leading Text’),
    Text(‘Middle Text’),
    Text(‘Trailing Text’),
  ],
);
```

#### Jetpack Compose

```Kotlin
Column {
  Text(“Top Text”)
  Text(“Middle Text”)
  Text(“Bottom Text”)
}

Row {
  Text(“Leading Text”)
  Text(“Middle Text”)
  Text(“Trailing Text”)
}
```

### Overlapping components

#### SwiftUI

```Swift
ZStack {
  Text(“Back”)
  Text(“Middle”)
  Text(“Front”)
}

```

#### Flutter


#### Jetpack Compose

```Kotlin
// Box children are placed on top of each other
Box(
  Text(“Back”)
  Text(“Middle”)
  Text(“Front”)
)

```

### Sizing views

#### SwiftUI

There are views that stick to the size of its content and there a views that fill all the available space.
The views sticking to the childs content will by default center itself in the parent.

<details>
  <summary>You can find a list here</summary>
  
  ##### Sticking to child size
  * Text
  * VStack
  * HStack
  * ZStack
  
  ##### Using full space of parent
  * Color
</details>

```Swift
// Limit color to the size
Color.blue
  .frame(width: 100, height: 100)
  
// Allow text to fill all the available space
Text(“Sample”)
  .frame(maxWidth: .infinity, maxHeight: .infinity)
```

#### Flutter

```Dart

// Ignores the size of the Container and while still fill the parent
Container(width: 100, height: 100, color: blue)

// Limit color to the size
Center(
  child: Container(width: 100, height: 100, color: blue),
)

// Force center to the full width and height of the parent
Center(
  child: Container(width: double.infinity, height: double.infinity, color: blue),
)
```

#### Jetpack Compose

```Kotlin
Box(
  Modifier.height(100.dp)
          .width(100.dp)
          .background(Color.Blue)
)

Text(
  text = “Sample”,
  modifier = Modifier
              .fillMaxWidth()
              .fillMaxHeight(),
)

```

### Aligning views

#### SwiftUI

```Swift
// Place a blue square with the size 50 x 50 in the center of a square 200 x 200
Color.blue
  .frame(width: 50, height: 50)
  .frame(width: 200, height: 200) // Here is the default value center if no other value is set
          
// Place a blue square with the size 50 x 50 in the top leading corner of a square 200 x 200
Color.blue
  .frame(width: 50, height: 50)
  .frame(width: 200, height: 200, alignment: .topLeading)
            
// Place a blue square with the size 50 x 50 in the top bottom trailing of a square 200 x 200
Color.blue
  .frame(width: 50, height: 50)
  .frame(width: 200, height: 200, alignment: .bottomTrailing)
  
// Center a text between elements with different sizes
// Multiple elements with infinity size will be sized the same when on the same level
HStack {
  Text(“Left”)
    .font(.footnote)
    .frame(maxWidth: .infinity, alignment: .trailing) // Fill the available space and align the text at the end
  Text(“Center”)
  Text(“Right”)
     .font(.title)
     .frame(maxWidth: .infinity, alignment: .leading) // Fill the available space and align the text at the start
}
```

#### Flutter

```Dart

```

#### Jetpack Compose

```Kotlin
// Place a blue square with the size 50 x 50 in the center of a square 200 x 200
Box(modifier = Modifier
        .width(200.dp)
        .height(200.dp),
        contentAlignment = Alignment.Center
) {
  Box(modifier = Modifier
        .width(50.dp)
        .height(50.dp)
        .background(Color.Blue)
  )
}

// Place a blue square with the size 50 x 50 in the top leading corner of a square 200 x 200
Box(modifier = Modifier
        .width(200.dp)
        .height(200.dp) // Default aligntment is top left corner
) {
  Box(modifier = Modifier
        .width(50.dp)
        .height(50.dp)
        .background(Color.Blue)
  )
}

// Place a blue square with the size 50 x 50 in the top bottom trailing of a square 200 x 200
Box(modifier = Modifier
        .width(200.dp)
        .height(200.dp),
        contentAlignment = Alignment.BottomEnd
) {
  Box(modifier = Modifier
        .width(50.dp)
        .height(50.dp)
        .background(Color.Blue)
  )
}

Box(modifier = Modifier
        .height(200.dp)
        .width(200.dp), 
    contentAlignment = Alignment.Center
) {
  Row(verticalAlignment = Alignment.CenterVertically) {
    Text(text = “Left”, fontSize = 40.sp, modifier = Modifier.fillMaxWidth().weight(1F), textAlign = TextAlign.End)
    Text(text = “Center”)
    Text(text = “Right”, modifier = Modifier.fillMaxWidth().weight(1F))
  }
}
```
