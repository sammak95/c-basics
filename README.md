# c-basics
This will be a dynamic repo, which will be used for whatever basic c functionalities, that I will come across


## How to include File Guards - Why to include Fileguards in C or C++ Header Files

File guards, also known as include guards, are a preprocessor mechanism used in C and C++ to prevent multiple inclusions of the same header file in a single translation unit. This helps avoid redefinition errors and reduces compilation time. Here's how they work:

### Basic Structure

An include guard typically looks like this:

```c
#ifndef HEADER_NAME_H
#define HEADER_NAME_H

// Declarations and definitions

#endif // HEADER_NAME_H
```

### Explanation of Components

1. **`#ifndef HEADER_NAME_H`**: This directive checks if `HEADER_NAME_H` has not been defined. If it hasn’t, the preprocessor includes the following code until it encounters the corresponding `#endif`.

2. **`#define HEADER_NAME_H`**: This defines the macro `HEADER_NAME_H`. Once defined, any subsequent attempts to include the same file will skip over the code between `#ifndef` and `#endif`.

3. **Content**: The code that you want to include only once goes here. This typically includes function declarations, class definitions, constants, etc.

4. **`#endif`**: This ends the conditional inclusion started by `#ifndef`.

### Example

Here’s a simple example of a header file:

```c
// my_header.h
#ifndef MY_HEADER_H
#define MY_HEADER_H

void myFunction();

#endif // MY_HEADER_H
```

### Usage

When you include `my_header.h` in multiple source files, the preprocessor will ensure that the contents are included only once, preventing issues like:

- Multiple definition errors.
- Increased compile time due to redundant parsing.

### Best Practices

1. **Unique Names**: Use unique names for the macro to avoid conflicts, especially in large projects or when using multiple libraries. A common practice is to use a combination of the project name and the header file name.

2. **Consistent Style**: Maintain a consistent naming and formatting style for your include guards to enhance readability.

### Alternative: `#pragma once`

An alternative to traditional include guards is the `#pragma once` directive, which is supported by many compilers. It serves the same purpose but is less error-prone since it does not require manual naming. Here's how it looks:

```c
// my_header.h
#pragma once

void myFunction();
```

While `#pragma once` is convenient, it may not be universally supported, so it's good to check compatibility with your target compilers.

In summary, include guards are a fundamental feature in C and C++ programming that help manage header file inclusions effectively.
