---
id: notes
title: Notes
---



## Assertions

The code contains numerous debug **assertions** which can be switched off by defining the preprocessor macro `NDEBUG`, see the [documentation of `assert`](http://en.cppreference.com/w/cpp/error/assert). In particular, note [`operator[]`](https://nlohmann.github.io/json/classnlohmann_1_1basic__json_a2e26bd0b0168abb61f67ad5bcd5b9fa1.html#a2e26bd0b0168abb61f67ad5bcd5b9fa1) implements **unchecked access** for const objects: If the given key is not present, the behavior is undefined (think of a dereferenced null pointer) and yields an [assertion failure](https://github.com/nlohmann/json/issues/289) if assertions are switched on. If you are not sure whether an element in an object exists, use checked access with the [`at()` function](https://nlohmann.github.io/json/classnlohmann_1_1basic__json_a674de1ee73e6bf4843fc5dc1351fb726.html#a674de1ee73e6bf4843fc5dc1351fb726).

## Numbers

As the exact type of a number is not defined in the [JSON specification](http://rfc7159.net/rfc7159), this library tries to choose the best fitting C++ number type automatically. As a result, the type `double` may be used to store numbers which may yield [**floating-point exceptions**](https://github.com/nlohmann/json/issues/181) in certain rare situations if floating-point exceptions have been unmasked in the calling code. These exceptions are not caused by the library and need to be fixed in the calling code, such as by re-masking the exceptions prior to calling library functions.

## Unicode

The library supports **Unicode input** as follows:

- Only **UTF-8** encoded input is supported which is the default encoding for JSON according to [RFC 7159](http://rfc7159.net/rfc7159#rfc.section.8.1).
- Other encodings such as Latin-1, UTF-16, or UTF-32 are not supported and will yield parse or serialization errors.
- [Unicode noncharacters](http://www.unicode.org/faq/private_use.html#nonchar1) will not be replaced by the library.
- Invalid surrogates (e.g., incomplete pairs such as `\uDEAD`) will yield parse errors.
- The strings stored in the library are UTF-8 encoded. When using the default string type (`std::string`), note that its length/size functions return the number of stored bytes rather than the number of characters or glyphs.

## Exceptions

**Exceptions** are used widely within the library. They can, however, be switched off with either using the compiler flag `-fno-exceptions` or by defining the symbol `JSON_NOEXCEPTION`. In this case, exceptions are replaced by an `abort()` call.

## Insertion Order

By default, the library does not preserve the **insertion order of object elements**. This is standards-compliant, as the [JSON standard](https://tools.ietf.org/html/rfc7159.html) defines objects as "an unordered collection of zero or more name/value pairs". If you do want to preserve the insertion order, you can specialize the object type with containers like [`tsl::ordered_map`](https://github.com/Tessil/ordered-map) ([integration](https://github.com/nlohmann/json/issues/546#issuecomment-304447518)) or [`nlohmann::fifo_map`](https://github.com/nlohmann/fifo_map) ([integration](https://github.com/nlohmann/json/issues/485#issuecomment-333652309)).

