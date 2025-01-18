# Flutter Notes

Flutter is a framework for creating UI for multiple platforms like Android, IOS, Web, Windows, MacOS, Linux etc.

## Widgets

A widget is a reusable piece of code that paints an UI component on the screen. like `Button`, `Text`, `Image` etc.

### MaterialApp

A widget that wraps number of widgets that are commonly required for material design application.

```dart
Widget build(BuildContext context) {
  return MaterialApp(
    home: Placeholder();
  );
}
```

### Scaffold

Implements basic material design visual layout structure. Like it adds default material style to `Text` widget.

```dart
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      appBar: AppBar(),
      body: Placeholder(),
      bottomNavigationBar: BottomAppBar(),
      floatingActionButton: FoatingActionButton(),
      floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
      backgroundColor: Colors.white
    );
  );
}
```

### Container

### Center

### Padding

### SizedBox

### Text

### Image

### FilledButton

### ElevatedButton

### TextButton

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
