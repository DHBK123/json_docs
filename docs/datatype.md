---
title: JSON as First-Class Datatype
---

## Overview

Here are some examples to give you an idea how to use the class.

Assume you want to create the JSON object

```json
{
  "pi": 3.141,
  "happy": true,
  "name": "Niels",
  "nothing": null,
  "answer": {
    "everything": 42
  },
  "list": [1, 0, 2],
  "object": {
    "currency": "USD",
    "value": 42.99
  }
}
```

With the JSON class, you could write:

```cpp
// create an empty structure (null)
json j;

// add a number that is stored as double (note the implicit conversion of j to an object)
j["pi"] = 3.141;

// add a Boolean that is stored as bool
j["happy"] = true;

// add a string that is stored as std::string
j["name"] = "Niels";

// add another null object by passing nullptr
j["nothing"] = nullptr;

// add an object inside the object
j["answer"]["everything"] = 42;

// add an array that is stored as std::vector (using an initializer list)
j["list"] = { 1, 0, 2 };

// add another object (using an initializer list of pairs)
j["object"] = { {"currency", "USD"}, {"value", 42.99} };
```

This all can be combined, so you could also write (which looks very similar to the JSON above):

```cpp
json j2 = {
  {"pi", 3.141},
  {"happy", true},
  {"name", "Niels"},
  {"nothing", nullptr},
  {"answer", {
    {"everything", 42}
  }},
  {"list", {1, 0, 2}},
  {"object", {
    {"currency", "USD"},
    {"value", 42.99}
  }}
};
```

Note that in all these cases, you never need to "tell" the compiler which JSON value you want to use.

## Details

In the rest of this section, we describe the details for each JSON type.

### Null

The `null` value can be created with the `nullptr` literal or the default constructor:

```cpp
json null1 = nullptr;
json null2;
```

### Boolean

Boolean values can be created with the literals `true` and `false`:

```cpp
json boolean1 = true;
json boolean2 = false;
```

### String

String values can be created from string literals, `std::string` values, or convertible types:

```cpp
json string1 = "string literal";
json string2 = std::string {"std::string value"};
const char ca[] = "character array";
json string3 = ca;
```

#### Notes

- Unicode
- MSVC types

### Number

### Array

### Object

If you want to be explicit or express some edge cases, the functions `json::array` and `json::object` will help:

```cpp
// a way to express the empty array []
json empty_array_explicit = json::array();

// ways to express the empty object {}
json empty_object_implicit = json({});
json empty_object_explicit = json::object();

// a way to express an _array_ of key/value pairs [["currency", "USD"], ["value", 42.99]]
json array_not_object = json::array({ {"currency", "USD"}, {"value", 42.99} });
```
