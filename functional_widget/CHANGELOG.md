## 0.4.0

- Now overrides `operator==` and `hashCode` on the generated class.

The behavior is that the following function:
```dart
@widget
Widget foo(int foo, int bar) {
    return Container();
}
```

now generates the following overides:

```dart
@override
int get hashCode => hashValues(foo, bar);

@override
bool operator ==(Object o) =>
    identical(o, this) || (o is Foo && foo == o.foo && bar == o.bar);
```

This is useful because overriding `operator==` prevents pointless rebuild when no parameter change.

## 0.3.0

-   Support function callbacks and generic functions:

```dart
@widget
Widget foo<T>(void onTap(T value)) {
    // do something
}
```

-   Updated support for `HookWidget` using new annotation `@hwidget`:

```dart
@hwidget
Widget foo() {
    final counter = useState(0);
    // do something
}
```

## 0.2.2

-   Readme update

## 0.2.1

-   Fix bug where types from `dart:ui` where generated as `dynamic`

## 0.2.0

-   Rename generator
-   Add documentation

## 0.1.0

-   Generate class documentation from the function documentation.
-   Pass down decorators from function parameter to class constructor

## 0.0.1

Initial release