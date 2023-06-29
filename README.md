# uuid4
A tiny C library for generating [uuid4](http://www.ietf.org/rfc/rfc4122.txt) strings. This module has been adapted from the [original author](https://github.com/rxi/uuid4) to instead use the hardware based random number generator in an ESP32 to generate the seed for the uuid4. The ESP32 RNG entropy source is enabled using the `bootloader_random_enable()` function. The [ESP32 RNG API reference can be found here](https://docs.espressif.com/projects/esp-idf/en/v4.4/esp32s3/api-reference/system/random.html).

### Usage
[uuid4.c](src/uuid4.c?raw=1) and [uuid4.h](src/uuid4.h?raw=1) should be
dropped into an existing project. The library contains two functions:
one to initialize the library and one to generate a uuid4 string and
store it in a buffer of at least `UUID4_LEN` in size.

```c
char buf[UUID4_LEN];
uuid4_init();
uuid4_generate(buf);
printf("%s\n", buf);
```

`uuid4_generate()` is not thread-safe.

### License
This library is free software; you can redistribute it and/or modify it
under the terms of the MIT license. See [LICENSE](LICENSE) for details.

