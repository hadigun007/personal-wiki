![Hadi-Banner](../hadi-banner.png)

# Programming Language Topics

### Topics

- Dart
    - [Dart SDK](#dart-sdk)
    - [Dart Exception and Error](#dart-exception-and-error)
- Java
- Typescript
- Golang
- Python
- [Solidity](./blockhcain/blockchain.md)



---




## Dart SDK

- [Core](#core)
    - [dart:async](#dartasync)
    - [dart:collection](#dart-sdk---collection)
    - [dart:convert](#dartconvert)
    - [dart:core](#dartcore)
    - [dart:developer](#dartdeveloper)
    - [dart:math](#dartmath)
    - [dart:typed_data](#darttyped_data)
- [VM](#vm)
    - [dart:cli](#dartcli)
    - [dart:ffi](#dartffi)
    - [dart:io](#dartio)
    - [dart:isolate](#dartisolate)
    - [dart:mirror](#dartmirror)
- [Web](#web)
    - [dart:html](#dartasync)
    - [dart:index_db](#dartcollection)
    - [dart:js](#dartconvert)
    - [dart:js_util](#dartcore)
    - [dart:svg](#dartdeveloper)
    - [dart:web_audio](#dartmath)
    - [dart:web_gl](#darttyped_data)

---

## Core
### dart:async
### dart:collection
### dart:convert
### dart:core
### dart:developer
### dart:math
### dart:typed_data
## VM
### dart:cli
### dart:ffi
### dart:io
### dart:isolate
### dart:mirror
## Web
### dart:html
### dart:index_db
### dart:js
### dart:js_util
### dart:svg
### dart:web_audio
### dart:web_gl

### Dart SDK - Collection
- [Introduction]()
- [Map](#map)
    - [HashMap]()
    - [LinkedHashMap]()
    - [SplayTreeMap]()
    - [UnmidifiableMapView]()
- [Set]()
    - [HashSet]()
    - [LinkedHashSet]()
    - [SplayTreeSet]()
    - [UnmodifiableSetView]()
- [Queue]()
    - [Queue]()
    - [ListQueue]()
    - [DoubleLinkedQueue]()
- [List]()
    - [UnmodifiableListView]()
- [LinkedList]()

---

## Introduction
Classes nad utilities that supplement the collection support in dart:core.
To use this library in your code:

``` dart
import 'dart:collection';
```
## Map
A finite mapping fom unique keys to their associated valus. Allows efficient lookup of the value associated with a key, if any, and iterating through the individual keys and values of the map. The Map interface has a number of implementations, including the following:
### HashMap
A hash-table based implementations of Map.\
\
The hashmap is unordered (the order of iteration is not guaranteed).\
\
The keys of hashmapmust have consistent ```Object.==``` and ```Object.hashCode``` implementations. This means that the ```==``` operator must define a stable equivalence relation on the keys (reflexive, symetric, transitive, and consistent over time), and that ashcode must be the same for objects that are considered equal by ```===```.\
\
Iterating the map's key value or entries (through foreach) may happen in any order. Tje iteration order only changes when the map is modified. Values are iterated in the same order as  their associated keys and values in parallel will give matching key and value pairs.\
\
**Notice:** Do not modify a map(add or remove while an operation is being performed on that map), for example in function called during a foreach or pitIfAbsent call, or while iterating the map(keys, values or entries).\
\
**Example:**
```dart
final Map<int, String> planets = HashMap(); // Is A HasmMap
```
To add data to a map, use ```operator[]=```, ``addAll`` or ```addEntries```.
**Example:**
```dart
planets[3] = 'Earth';
planets.addAll({4: 'Mars'});

final gasGiants = {6: 'Jupiter', 5: 'Saturn'};
planets.addEntries(gassGiants.entries)
print(planets); // fx {5: Saturn, 6: Jupiter, 3: Earth, 4: Mars }
```

To check if the map is empty, use ```isEmpty``` or ```isNotEmpty```. To find the number of map entries, use ```length```.

``` dart
final isEmpty = planets.isEmpty; // false
final length = planets.length; // 4
```

The ```foreach``` iterates through all entries of map.

```dart
planets.forEach((key, val){
    print('$key \t $value')
    // 5    Saturn
    // 4    Mars
    // 3    Earth
    // 6    Jupiter
})
```

To Check wheter the maps has an entry with specific key, use ```containsKey```.

```dart
final keyOneExist = planets.containsKey(4) // true
final keyFiveExist = planets.containsKey(1) // false
```

To check wheter the map has an entry with a specific use ```containsValue```.

```dart
final marsExist = planets.containsValue('Mars') // true
final keyFiveExist = planets.containsValue('Venus') // false
```

To remove an entry with a specific key, use ```remove```.

```dart
final removable = planets.remove(5);
print(removeValue); // Jupiter
print(planets) // fx {4: Mars, 3: Earth 5: Saaturn}
```

To remove multiple entries at the same time, based on their keys and values, use ```removeWhere```.

```dart
planets.removeWhere((key, value) => key == 5);
print(planets); // fx {4: Saturn, 8: Neptune, 3: Earth}
```

To conditionally add or modify  a value for a specific key. depedending on wheter there already is an entry with that key, use ```pubIfAbsent``` or ```update```.
```dart
planets.update(4, (v) => 'Saturn');
planets.update(8, (v) => '', ifAbsent: () => 'Neptune');
planets.putIfAbsent(4, () => 'Another Saturn');
print(planets); // fx: {4: Saturn, 8: Neptune, 3: Earth}
```

To update the values of all keys, based on the existing key and value, use ```updateAll```.

```dart
planets.updateAll((key, value) => 'X');
print(planets) // fx {8: X, 3: X, 4: X}
```

To remove all entries and empty the map, use ```clear```.

```dart
planets.clear();
print(planets); // {}
print(planet.isEmpty) // true
```
---

## Dart Exception and Error

### Exception
- DeferredLoadException
- FormatException
- IntegerDivisionByZeroException
- IOException
- IsolateSpawnException
- NullRejectionException
- OSErrorTimeoutException

### Error
- AbstractClass
- InstantiationError
- ArgumentError
- AssertionError
- AsyncError
- ConcurrentModificationError
- JsonUnsupportedObject
- ErrorNoSuchMethodError
- OutOfMemoryError
- ParallelWaitError
- RemoteError
- StackOverflowError
- StateError
- TypeError
- UnimplementedError
- UnsupportedError



---

src: [Dart Documentation](https://api.dart.dev/stable/3.0.7/index.html)

---
<p style="color: grey">created by <b  style="color:white">Hadi Gunawan @2023</b></p>