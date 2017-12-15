---
title: Member Functions
---

## Object Inspection

JSON distinguishes the following types:

- primitive types:
  - null
  - boolean
  - string
  - number
- structured types:
  - array
  - object

The type of a `json` value can be queried with the following functions:

```cpp
bool is_null();
bool is_boolean();
bool is_string();
bool is_number();
bool is_array();
bool is_object();
bool is_primitive();
bool is_structured();
```

Furthermore, the library distinguishes the following number types:

- (signed) integer
- unsigned integer
- floating-point

In addition to `is_number()` the following functions help to distinguish the number types:

```cpp
bool is_number_integer();
bool is_number_unsigned();
bool is_number_float();
```

## Value Access

## Element Access

## Lookup

## Iterators

## Capacity

## Modifiers

## Comparison
