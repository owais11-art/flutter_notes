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

### FractionallySizedBox

A widget that can size relatively to the space available. Sizes can be changed through `widthFactor` and `heightFactor` properties. `0` means zero percent and `1` means hundred percent.

```dart
FractionallySizedBox(
  widthFactor: 0.5, // 50%
  height: 0.413 // 41.3%
  child: Container(...)
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

A widget that arranges its children vertically. In this widget y-axis is considered main axis and x-axis is considered cross axis. Children can be aligned in main axis through `mainAxisAlignment` property and in cross axis through `crossAxisAlignment` property. Spacing between children can be set through `spacing` property. By default `Column` takes the maximum space available vertically but if we want `Column` to take the space equal to the content inside it we can use `mainAxisSize` property and set it to `MainAxisSize.min`. By default `Column` lays out its children from top to bottom, to reverse this order use `verticalDirection` property and set it to `VerticalDirection.up`.

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.start,
  crossAxisAlignment: CrossAxisAlignment.center,
  spacing: 10.0,
  mainAxisSize: MainAxisSize.max,
  verticalDirection: VerticalDirection.down,
  children: [...]
);
```

### Row

A widget that arranges its children horizontally. In this widget x-axis is considered main axis and y-axis is considered cross axis. Children can be aligned in main axis through `mainAxisAlignment` property and in cross axis through `crossAxisAlignment` property. Spacing between children can be set through `spacing` property. By default `Row` takes the maximum space available horizontally but if we want `Row` to take the space equal to the content inside it we can use `mainAxisSize` property and set it to `MainAxisSize.min`.

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.start,
  crossAxisAlignment: CrossAxisAlignment.center,
  spacing: 10.0,
  mainAxisSize: MainAxisSize.max,
  children: [...]
);
```

### Expanded

A widget that takes the remaining space within `Column` or `Row` after, unexpanded children has taken their space. If we have more than one `Expanded` widgets then by default remaining space will distributed equally between them. We can set the fraction of space that an `Expanded` widget can take from the remaining space through `flex` property.

```dart
Expanded(
  flex: 1,
  child: Container(...)
);
```

### Stack

A widget that arranges its children by putting them on top of one another. By default its children are positioned at top left of the `Stack`, this can be changed through `alignment` property. To control the sizing of children inside `Stack` use `fit` property. `fit` can take one of three values `StackFit.loose`, `StackFit.expand`, `StackFit.passthrough`.

`StackFit.loose` means that the children can have dimensions between 0x0 and the dimensions of `Stack` e.g; if `Stack` is 300x400 then children can have dimensions between 0x0 and 300x400.

`StackFit.expand` means that children will take maximum dimension available. If `Stack` is 300x400 then children will also be 300x400.

`StackFit.passthrough` means that dimensions are passed to the children unmodified.

```dart
Stack(
  alignment: Alignment.topCenter,
  fit: StackFit.loose,
  children: [...]
);
```

### Positioned

A widget that can position itself within `Stack`. Positions can be changed through `top`, `bottom`, `left`, `right` properties. Dimensions can be changed through `width` and `height` properties.

```dart
Positioned(
  top: 10.0,
  bottom: 10.0,
  left: 10.0,
  right: 10.0,
  width: 200.0,
  height: 250.0,
  child: Text("Positioned Text!!!")
);
```

### ListView

A widget that paints a scrollable list on the screen. By default it is scrolled vertically but we can change it through `scrollDirection` property by setting it to `Axis.horizontal`. User scrolls the list from top to bottom or left to right depending on the scroll direction but setting `reverse` property to `true`, user will scroll the list from bottom to top or right to left depending on the scroll direction. To set the extent(size in scroll direction) of children use `itemExtent` property. For creating `ListView` dynamically use `ListView.builder` and provide `itemCount` number of items in list and `itemBuider` callback for creating single item. For listening to the scrolling of `ListView` assign `ScrollController` object to the `controller` property and call `addListener` method on the object which takes a callback as an argument which will be executed every time `ListView` is scrolled.

```dart
class _MyListView extends State<MyListView>{
  final List<Post> _posts = [];
  final ScrollController _scrollController = ScrollController();
  /*
    _scrollController.jumpTo(<position>) -> jumps to given position
    _scrollController.animateTo(<position>, <duration>, <curve>) -> animates to given position
    _scrollController.moveTo(<position>, <duration>, <curve>) -> animates to given position if duration is given else jumps to the given position
  */
  void initState() {
    _scrollController.addListener(() {
      var offset = _scrollController.offset; // returns how much has been scrolled in pixels
      var sameAsOffset = _scrollController.position.pixels; // also returns how much has been scrolled in pixels
      var minScrollExtent = _scrollController.position.minScrollExtent; // returns how much has been scrolled when ListView is at start
      var maxScrollExtent = _scrollController.position.maxScrollExtent; // returns how much has been scrolled when ListView is at end
    });
    super.initState();
  }
  void dispose() {
    _scrollController.dispose();
    super.dispose();
  }
  Widget build(BuildContext context) {
    return ListView.builder(
      scrollDirection: Axis.vertical,
      reverse: false,
      itemExtent: 40.0,
      itemCount: _posts.length,
      itemBuilder: (context, index) {...},
      controller: _scrollController
    );
  }
}
```

### GridView

A widget that creates a scrollable with multiple number of columns. Padding to the `GridView` is given through `padding` property. To change scroll direction use `scrollDirection` property. User scrolls the `GridView` from top to bottom or left to right depending on the scroll direction but setting `reverse` property to `true`, user will scroll the `GridView` from bottom to top or right to left depending on the scroll direction. To create a grid with fixed number of columns use `GridView.count`. To set the number of columns use `crossAxisCount` property. To create a grid based on the given extent for each child use `GridView.extent` ***extent is width when scroll direction is vertical and height when scroll direction is horizontal***. To set the extent for each child use `maxCrossAxisExtent`. We can also give spacing between children in main and cross axis using `mainAxisSpacing` and `crossAxisSpacing` respectively. To create a grid dynamically use `GridView.builder` and provide number of children through `itemCount` property and `itemBuilder` callback that is responsible for creating single item. To create `GridView.builder` with fixed number of columns use `gridDelegate` property and assign it `SliverGridDelegateWithFixedCrossAxisCount` object and pass `crossAxisCount` as argument to this object. To create `GridView.builder` based on the given extent for each child use `gridDelegate` property assign it `SliverGridDelegateWithMaxCrossAxisExtent` object and pass `maxCrossAxisExtent` as argument to this object. Both `SliverGridDelegateWithFixedCrossAxisCount` and `SliverGridDelegateWithMaxCrossAxisExtent` can take `mainAxisSpacing` and `crossAxisSpacing` as parameters.

```dart
GridView.count(
  padding: EdgeInsets.all(8.0),
  crossAxisCount: 3,
  mainAxisSpacing: 10.0,
  crossAxisSpacing: 10.0,
  children: [...]
);

GridView.extent(
  padding: EdgeInsets.all(8.0),
  maxCrossAxisExtent: 150.0,
  mainAxisSpacing: 10.0,
  crossAxisSpacing: 10.0,
  children: [...]
);

// Dynamic fixed columns
GridView.builder(
  padding: EdgeInsets.all(8.0),
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 3,
    mainAxisSpacing: 10.0,
    crossAxisSpacing: 10.0,
  ),
  itemCount: _images.length,
  itemBuilder: (context, index) {...}
);

// Dynamic based on extent
GridView.builder(
  padding: EdgeInsets.all(8.0),
  gridDelegate: SliverGridDelegateWithMaxCrossAxisExtent(
    maxCrossAxisExtent: 150.0,
    mainAxisSpacing: 10.0,
    crossAxisSpacing: 10.0,
  ),
  itemCount: _images.length,
  itemBuilder: (context, index) {...}
);
```

### ClipRect

This widget prevents child from painting outside its bounds. E.g; If we have an `Image` inside `Center` and `widthFactor` of `Center` is less than `1.0` then `Image` will overflow from `Center`, to prevent this wrap `Center` with `ClipRect`.

```dart
ClipRect(
  child: Center(
    widthFactor: 0.5,
    child: Image.network(...)
  )
);
```

### ClipRRect

This is same as `ClipRect` but it also lets us create rounded border.

```dart
ClipRRect(
  borderRadius: BorderRadius.circular(8.0),
  child: ...
);
```

### TextField

This widget lets user enter data. It can be styled through `decoration` property. To listen to the changes while user is entering data use `onChanged` callback. To listen when user is done entering data by clicking done button on keypad use `onSubmitted` callback. To bind the `TextField` with a state, so that when user enters something in `TextField` that gets assigned to the state, create a state of type `TextEditingController` and assign it to the `controller` property of `TextField`. To control the focus state of `TextField` use `focusNode` property and assign it an object of type `FocusNode`. To hide the text inside `TextField` like in passwords use `obscureText` and set it to `true`. For styling text in `TextField` use `style` property.

```dart
TextField(
  controller: _myController, // Object of type TextEditingController
  focusNode: _myFocusNode, //Object of type FocusNode
  style: TextStyle(fontSize: 18.0),
  decoration: InputDecoration(
    hintText: "Enter Something...", // placeholder text
    hintStyle: TextStyle(color: Colors.black.withAlpha(90)), // styles for hintText
    labelText: "Username", // Text for label of TextField
    labelStyle: TextStyle(...), // styles for labelText
    floatingLabelStyle: TextSTyle(...) // style is applied when labelText is floating at top of TextField
    floatingLabelBehavior: FloatingLabelBehavior.auto, // manages the behaviour of labelText whether it always be floating or never or have default behavior
    floatingLabelAlignment: FloatingLabelAlignment.start, // Placement of labelText either start or center
    border: OutlineInputBorder(borderSide: BorderSide.none)), // Border of TextField
    focusBorder: OutlineInputBorder(borderSide: BorderSide.none)), // Border when focused
    errorBorder: OutlineInputBorder(borderSide: BorderSide.none)), // Border when error
    enabledBorder: OutlineInputBorder(borderSide: BorderSide.none)), // Border when enabled
    disabledBorder: OutlineInputBorder(borderSide: BorderSide.none)) // Border when disabled
  ),
  onChanged: (value) {...},
  onSubmitted: (value) {...},
  onTapOutside: (e) => _myFocusNode.unfocus()
);
```

### Form

A widget that can contain multiple form fields. It makes form handling convenient and easy. Using this widget we can easily do form validations and form resets. For that we need to assign `GlabalKey` of generic type `FormState` to `key` property of `Form`. To validate form fields we can execute `validate` method on `_formKey.currentState`.

```dart
Form(
  key: _formKey, // Key of type GlobalKey<FormState>
  child: ...
);
```

### TextFormField

It is similar to `TextField` but is commonly use as descendant of `Form`. It also provides a way for validation through `validator` callback. `onSaved` callback is used to save the value of this field in a state. In this widget use `onFieldSubmitted` instead of `onSubmitted` callback.

```dart
TextFormField(
  validator: (value) {...},
  onSaved: (value) {...},
  onFieldSubmitted: (value) {...}
);
```

### DatePicker

This widget displays a material themed date picker. To show date picker we have to execute `showDatePicker` function which requires `context`, `initialDate`, `firstDate` and `lastDate` properties. It is an asynchronous function it returns the selected date if user clicks confirm on date picker and returns `null` if user clicks cancel on date picker. To change styling we can use `DatePickerThemeData` inside `ThemeData`.

```dart
FilledButton(
  onPressed: () async {
    var dateSelected = await showDatePicker(
      context: context,
      initialDate: DateTime.now(),
      firstDate: DateTime(2000),
      lastDate: DateTime(2100),
      barrierColor: Colors.black.withAlpha(90), // Modal overlay color
      builder: (context, child) => Theme(
        // For dark theme use ThemeData().dark().copyWith()
        // These styles can also be applied in MaterialApp's theme and darkTheme properties
        data: ThemeData(
          datePickerTheme: DatePickerThemeData(
            headerForegroundColor: Color(0xFF041611),
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(8.0)
            ),
            backgroundColor: Color(0xFFdcf9ef),
            dividerColor: Color(0xFF137655).withAlpha(100),
            weekdayStyle: TextStyle(color: Color(0xFF041611)),
            inputDecorationTheme: InputDecorationTheme(
              labelStyle: TextStyle(color: Color(0xFF041611)),
              floatingLabelStyle: TextStyle(color: Color(0xFF041611)),
              focusedBorder: OutlineInputBorder(borderSide: BorderSide(color: Color(0xFF137655))),
              border: OutlineInputBorder(borderSide: BorderSide(color: Color(0xFF041611)))
            ),
            cancelButtonStyle: ButtonStyle(
              foregroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFF137655)) 
            ),
            confirmButtonStyle: ButtonStyle(
              foregroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFF137655)) 
            ),
            todayBackgroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFF4a20cb)),
            todayForegroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFFdcf9ef)),
            yearForegroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFF041611)),
            dayForegroundColor: WidgetStateProperty.resolveWith<Color>(
                (widgetState) => Color(0xFF041611))
          )
        ),
        child: child!
      )
    );
  }
  child: Text("Date Picker")
);
```

### DropdownButtonFormField

### DropdownMenuItem

