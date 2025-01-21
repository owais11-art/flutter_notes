# Flutter Notes

Flutter is a framework for creating UI for multiple platforms like Android, IOS, Web, Windows, MacOS, Linux etc.

## Widgets

A widget is a reusable piece of code that paints an UI component on the screen. like `Button`, `Text`, `Image` etc.

### MaterialApp

A widget that wraps number of widgets that are commonly required for material design application. It is the root widget of apps using material design and it is built upon `WidgetsApp`. It provides default material design theme to apps and also allows customization of the theme through `theme` property using `ThemeData`. It also handles routing through `routes` property. It enables the use of material widgets like `Scaffold`, `AppBar` etc. And it also handles localization.

```dart
Widget build(BuildContext context) {
  return MaterialApp(
    theme: ThemeData(),
    home: Placeholder(),
  );
}
```

### Scaffold

Implements basic material design visual layout structure. Like it adds default material style to `Text` widget. It provides the structure to the app screen by containing `AppBar`, `BottomAppBar`, `body`, `Drawer`, `FloatingActionButton` etc.

```dart
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      appBar: AppBar(),
      body: Placeholder(),
      bottomNavigationBar: BottomAppBar(),
      floatingActionButton: FoatingActionButton(),
      floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
      backgroundColor: Colors.white,
      drawer: Drawer()
    );
  );
}
```

### Container

A widget rendered as a box on screen with properties to change its size through `width` and `height` properties add padding and margin through `padding` and `margin` properties apply styles through `decoration` property. It usually wraps another widget that does not have any of the mentioned properties like `Column`, `Row` etc.

```dart
Container(
  width: 100,
  height: 100,
  padding: EdgeInsets.all(8.0),
  margin: EdgeInsets.all(8.0),
  alignment: Alignment.center,
  decoration: BoxDecoration(
    color: Colors.blue,
    gradient: LinearGradient(),
    border: Border.all(color: Colors.yellow, width: 1, style: BorderStyle.solid),
    borderRadius: BorderRadius.circular(6.0),
    boxShadow: [BoxShadow(color: Colors.blue, offset: Offset(5, 5), blurRadius: 0, spreadRadius: 0)]
  ),
  child: Column()
);
```

### Center

A widget that centers it child horizontally and vertically. Width and Height of this widget can be changed through `widthFactor` and `heightFactor` properties.

`widthFactor` -> Sets width of `Center` widget by multiplying its widthFactor `2.0 in given code` with the width `100 in given code` of its child. In below code width of `Center` widget will be `2.0 * 100 = 200`.

`heightFactor` -> Sets height of `Center` widget by multiplying its heightFactor `3.0 in given code` with the height `100 in given code` of its child. In below code height of `Center` widget will be `3.0 * 100 = 300`.

```dart
Center(
  widthFactor: 2.0,
  heightFactor: 3.0,
  child: Container(
    color: Colors.yellow,
    width: 100,
    height: 100
  )
);
```

### Padding

A widget that adds padding to its child.

```dart
Padding(
  padding: EdgeInsets.all(8.0),
  child: Text("Hello Flutter!!!")
);
```

### SizedBox

A widget with specified width and height. If given a child then the child will be forced to have that specified width and height.

```dart
SizedBox(
  width: 500,
  height: 500,
  child: Card(child: Text("This is a Card!!!"))  // This card will be forced to have the size of 500 x 500.
);
```

### Text

A widget that displays text on screen. The text can be styled through `style` property. We can use `textAlign` property to align text. Text direction can be changed through `textDirection` property. We can set maximum lines through `maxLines` property. We can control the overflow text style through `overflow` property. By default if text is large it will be wrapped in multiple lines, to disable it we can set `softWrap` to `false`.

```dart
Text(
  "Hello Flutter!!!",
  textAlign: TextAlign.center,
  textDirection: TextDirection.rtl,
  maxLines: 1,
  overflow: TextOverflow.clip,
  softWrap: false,
  style: TextStyle(
    color: Colors.black,
    fontFamily: "Poppins",
    fontSize: 16,
    fontWeight: FontWeight.bold,
    fontStyle: FontStyle.italic
  )
);
```

### Image

A widget to display image. Image source can be taken from assets, network, file, memory. To inscribe image inside its parent use `fit` property.

```dart
Image(
  image: NetworkImage("url"),
  fit: BoxFit.cover
);
```

### FilledButton

A widget that displays a button with filled background. Its styles can be changed through `style` property using `FilledButton.styleFrom` object. It has `onPressed` property which takes a callback as value and executes it when user presses the button.

```dart
FilledButton(
  onPressed: () {print("Button Pressed!!!")},
  style: FilledButton.styleFrom(
    backgroundColor: Colors.blue,
    foregroundColor: Colors.white,
    elevation: 5,
    shadowColor: Colors.yellow,
    padding: EdgeInsets.all(10.0),
    side: BorderSide(color: Colors.purple, width: 3.0)
  ),
);
```

### ElevatedButton

A widget that displays a button with elevation. Its styles can be changed through `style` property using `ElevatedButton.styleFrom` object. It has `onPressed` property which takes a callback as value and executes it when user presses the button.

```dart
ElevatedButton(
  onPressed: () {print("Button Pressed!!!")},
  style: ElevatedButton.styleFrom(
    backgroundColor: Colors.blue,
    foregroundColor: Colors.white,
    elevation: 5,
    shadowColor: Colors.yellow,
    padding: EdgeInsets.all(10.0),
    side: BorderSide(color: Colors.purple, width: 3.0)
  ),
);
```

### TextButton

A widget that displays a button with text only and no default styles for button. Its styles can be changed through `style` property using `TextButton.styleFrom` object. It has `onPressed` property which takes a callback as value and executes it when user presses the button.

```dart
TextButton(
  onPressed: () {print("Button Pressed!!!")},
  style: TextButton.styleFrom(
    backgroundColor: Colors.blue,
    foregroundColor: Colors.white,
    elevation: 5,
    shadowColor: Colors.yellow,
    padding: EdgeInsets.all(10.0),
    side: BorderSide(color: Colors.purple, width: 3.0)
  ),
);
```

### Column

### Row

### Stack

### Positioned

### ClipRRect

### TextField

### Form

### TextFormField

### DropdownButtonFormField

### DropdownMenuItem

### GestureDetector
