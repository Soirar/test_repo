# WymonOrion Naming Conventions

These naming conventions apply to the whole WymonOrion project, meaning both
C++ and Python code. They are compliant with the Python naming conventions
as described in [PEP 0008][pep_0008].

## General

* Please, for god's sake, use your brain.

* Be consistent.

* Go for readability.

* Use descriptive names, avoid abbreviations.

    Don't try to save horizontal space, go for understandability. Use only common
    abbreviations. Don't abbreviate by deleting letters in the middle.

    Yes:

    ```
    file_writer -> descriptive name  
    num_errors -> 'num' is a common abbreviation  
    num_http_connections -> 'HTTP' is a well known abbreviation  
    ```

    No:

    ```
    pc_reader -> 'pc' may stand for a lot of things
    cstmr_id -> deleting letters within the word
    ```

* Avoid name collisions not by abbreviating the name, but by adding an
  underscore (`_`) at the end.

    Yes:
    
    ```
    class becomes class_ -> name is still clearly readable
    struct becomes struct_
    ```

    No:

    ```
    class becomes clss -> abbreviated within the word
    struct becomes strct 
    ```

* Don't capitalize acronyms, treat them as regular words.

    Yes:

    ```
    get_url() -> 'URL' is in same case as rest of name
    HttpConnection
    ```

    No:

    ```
    get_URL()
    HTTPConnection
    ```

## Folders, Modules and Namespaces

* Use all-lowercase and short words, avoid separating with underscores (`_`).

    Pick short and descriptive names. Make use of underscores only where it
    tremendously improves readability.

    Yes:


    ```
    graphics
    source
    devtools -> 'dev' is commonly known, no underscore separation
    ```

    No:
    
    ```
    gfx -> 'gfx' is not a widely known abbreviation
    src -> although 'src' is commonly known, 'source' is more readable
    dev_tools
    ```

* Folder, module and namespace names resemble each other.

    Yes:
    
    ```
    Namespace: system
    Module: system
    Folder: system
    -> system::error(), system.error(), system/error.hpp
    ```

    No:

    ```
    Namespace: sys
    Module: system
    Folder: System
    -> sys::error(), system.error(), System/error.hpp
    ```

* A C++ extension module with accompanying Python module has the same name, but 
  with an underscore (`_`) as prefix.

    It may occur that a C++ extension module is further extended using Python, 
    for instance to provide extra functionality. Both modules should have the 
    same name, but to distinguish them, the C++ extension module should have an 
    underscore (`_`) as prefix. The module imported will be the one without the 
    prefix.

    Yes:
    
    ```
    C++ extention module: _system
    Python module: system
    -> import system
    ```
    
    No:
    
    ```
    C++ extention module: system_cpp
    Python module: system
    -> import system
    ```

## Files

* Use all-lowercase and separate with underscores (`_`).

    Yes:

    ```
    http_connector.hpp
    find_item.cpp
    ```

    No:

    ```
    httpConnector.hpp
    HTTPConnector.hpp
    Find_Item.cpp
    ```

* Name files after the most significant piece of code they contain.

* Header files end in `.hpp`.

* Source files end in `.cpp`.

* For files containing templates and inline functions you don't want to put
  into an `.hpp` file, use the file extention `.inl` ('inline code').

* Give a header declaring and a source file defining a piece of code the same
  name.

    Yes:

    ```
    foo_bar.hpp, foo_bar.cpp -> declaring and defining the class 'FooBar'
    ```

    No:

    ```
    foo_bar_decl.hpp, foo_bar_def.cpp -> different names for the pair of files
    ```

## Types

* Use [UpperCamelCase][upper_camel_case] for classes, structs, typedefs and 
  template parameters.

    Yes:

    ```
    MyClass
    FooBarMe 
    ```

    No:

    ```
    My_Class -> no underscores
    fooBar
    ```

## Functions

* Use all-lowercase and separate with underscores (`_`).
    
    Yes:
    
    ```
    get_table_entry()
    set_value()
    ```

    No:

    ```
    getTableEntry()
    SetValue()
    ```

## Variables

* Use all-lowercase and separate with underscores (`_`).

    Yes:

    ```
    table_content
    file_name
    ```

    No:

    ```
    tableContent
    FileName
    ```

* Add the prefix `m_` for member variables.

    Yes:

    ```
    m_tables
    m_class
    ```

    No:

    ```
    class_ -> technique already used to avoid name collisions, may cause some
    ```

* Add the prefix `g_` for global variables. No, better, avoid them all along.

## Constants

* Use all-uppercase and separate with underscores (`_`).

    Yes:

    ```
    EXAMPLE_CONSTANT
    FOO_BAR
    ```

    No:

    ```
    ExampleConstant
    Foo_bar
    ```

## Exceptions

* Use [UpperCamelCase][upper_camel_case] for excpetion names and add the suffix
  `Error`.

    Since exceptions are classes, they are also types and are named in
    the same way.

    Yes:

    ```
    OutputError
    InternetConnectionError
    ```

    No:

    ```
    OutputException -> wrong suffix
    bad_internet_connection -> missing suffix
    ```

## Enumerations

* Use [UpperCamelCase][upper_camel_case] for enumeration names.

    The enumeration name is a type and is therefore named in the same way.

    Yes:

    ```
    UrlTableErrors {...};
    AlternateError {...};
    ```

    No:

    ```
    URL_TABLE_ERRORS {...};
    alternateError {...};
    ```

* Use all-uppercase and separate with underscores (`_`) for enumeration values.

    The enumeration values are constants and are therefore named in the same 
    way.

    Yes:

    ```
    UrlTableErrors {OK, NOT_FOUND};
    AlternateError {UNDEFINED, NONE};
    ```

    No:

    ```
    UrlTableErrors {ok, not_found};
    AlternateError {Undefined, NotFound};
    ```

## Macros

* Use all-uppercase and separate with underscores (`_`).

    Yes:

    ```
    #define ROUND(x) ...
    #define ANSWER_TO_LIFE 42
    ```

    No:

    ```
    #define Round(x) ...
    #define answer_to_life 42
    ```

---

Based on:  
[Google C++ Style Guide][google_cpp_guide]  
[PEP 0008 -- Style Guide for Python Code][pep_0008]

[google_cpp_guide]: https://google.github.io/styleguide/cppguide.html#Naming, "Google C++ Style Guide"
[pep_0008]: https://www.python.org/dev/peps/pep-0008/#naming-conventions, "Style Guide for Python Code"
[upper_camel_case]: http://c2.com/cgi/wiki?UpperCamelCase, "aka PascalCase"
