# Lua programming language

Some hints form *Roberto Ierusalimsch*y tutorial and a small collection of snippets collected during the **lectures**
- [Lua programming language](#lua-programming-language)
  - [Chunks](#chunks)
  - [Global variables](#global-variables)
  - [Local variables](#local-variables)
  - [About lexical conventions](#about-lexical-conventions)
  - [Commenting](#commenting)
  - [Types and values](#types-and-values)
    - [Type function](#type-function)
  - [Repeat](#repeat)
  - [Errors](#errors)
  - [Error Handling and Exceptions](#error-handling-and-exceptions)
- [Professor's snippets](#professors-snippets)



## Chunks

A chunk is simply a sequence of statements (each file and sequence of statemens that LUA executes).
A semicolon may **optionally** follow any statement. 
> **Convention:** use semicolons only to separate two or more statements written in the same line  

```Lua   
    a = 1
    b = a*2
    
    a = 1;
    b = a*2;
    
    a = 1 ; b = a*2
    
    a = 1   b = a*2    -- ugly, but valid
```

## Global variables 
Global variables **do not need declarations**. You simply assign a value to a global variable to create it. It is not an error to access a non-initialized variable; you just get the special value nil as the result:

```Lua   
    print(b)  --> nil
    b = 10
    print(b)  --> 10
```
Usually you **do not need** to **delete** global variables; if your variable is going to have a short life, you should use a `local` variable. But, if you need to delete a global variable, just assign `nil` to it:

```Lua 
    print(b)  --> nil**
```
After that, it is as if the variable had never been used. In other words:
> A **global variable** is existent **if (and only if)** it has a **non-nill** value.

## Local variables 
A local variables have their scope limited to the block where they are declared.
```Lua
    x = 10
    local i = 1        -- local to the chunk
    
    while i<=x do
      local x = i*2    -- local to the while body
      print(x)         --> 2, 4, 6, 8, ...
      i = i + 1
    end
    
    if i > 20 then
      local x          -- local to the "then" body
      x = 20
      print(x + 2)
    else
      print(x)         --> 10  (the global one)
    end
    
    print(x)           --> 10  (the global one)
```

## About lexical conventions

You should avoid identifiers starting with an underscore followed by one or more uppercase letters (e.g., `_VERSION`); they are reserved for special uses in Lua. 
> convention: reserve the identifier `_` (a single underscore) for a **dummy variable**.

## Commenting 

A comment starts anywhere with a double hyphen (`--`) and runs **until** the end of the line. 
Lua also offers block comments, which start with `--[[` and run until the corresponding `]]`. 

> **WARNING:** when we want to comment out a piece of code, is to write the following:

``` Lua
   --[[
    print(10)         -- no action (comment)
    --]]
```
Now, if we add a single hyphen to the first line, the code is in again:
``` Lua
    ---[[
    print(10)         --> 10
    --]]
```
Hence:
* In the first example, the `--` in the last line is still inside the block comment. 
* In the second example, the sequence `---[[` **does not start a block comment**; so, the print is outside comments. In this case, the **last line** *becomes* an independent comment, as it starts with --.

## Types and values 

There are eight basic types in Lua:

1. **nil**:
   Nil is a *type* with a *single* value, nil, whose main property is to be *different* from *any* other value. As we have seen, a global variable has a *nil* value by *default*, before a first assignment, and **you can assign** nil to a **global** variable to **delete** it. Lua uses nil as a kind of non-value, to represent the **absence** of a useful value.

2. **boolean**
   The boolean type has two values, **false** and **true**, which represent the traditional boolean values. Moreover In Lua, any value may represent a condition.
   > Conditionals (such as the ones in control structures) consider **false** and **nil** as **false** and **anything else** as **true**. Also, Lua considers both **zero** and the **empty string** as **true** in *conditional tests *
3. number 
4. **string**
   A sequence of characters. Lua is eight-bit clean hence  you can store any binary data **into** a string.  Strings in Lua are **immutable** values. You cannot change a character inside a string BUT, you create a new string with the desired modifications, as in the next example:
    ```Lua    
        a = "one string"
        b = string.gsub(a, "one", "another")  -- change string parts
        print(a)       --> one string
        print(b)       --> another string
    ```

    Strings in Lua are subject to **automatic memory management**, like all Lua objects. That means that you do not have to worry about **allocation** and **deallocation** of **strings**; Lua handles this for you. A string may contain a single letter or an entire book. Lua handles long strings quite efficiently
    We can delimit literal strings by matching single or double quotes:
    ```Lua
        a = "a line"
        b = 'another line'
    ```
    you should use always the same kind of quotes!
    Lua provides **automatic conversions** between numbers and strings at run time. Any numeric operation applied to a string tries to convert the string to a number:
    ```Lua
        print("10" + 1)           --> 11
        print("10 + 1")           --> 10 + 1
        print("-5.3e-10"*"2")     --> -1.06e-09
        print("hello" + 1)        -- ERROR (cannot convert "hello")
    ```
    The `..` is the **string concatenation operator** in Lua. When you write it right after a numeral, you must separate them with a space; otherwise, Lua thinks that the first dot is a decimal point.

    ```Lua
     print(10 .. 20)        --> 1020
    ```
    Despite those automatic conversions, strings and numbers are **different** things. A comparison like 10 == "10" is always false, because 10 is a number and "10" is a string. 
    > If you need to convert a string to a number *explicitly*, you can use the function `tonumber`, which returns **nil** if the string **does not denote** a proper number:
    ```Lua
        line = io.read()     -- read a line
        n = tonumber(line)   -- try to convert it to a number
        if n == nil then
        error(line .. " is not a valid number")
        else
        print(n*2)
        end
    ```
    To convert a number to a string, you can call the function `tostring` or concatenate the number with the empty string:
    ```Lua
        print(tostring(10) == "10")   --> true
        print(10 .. "" == "10")       --> true
    ```


5. userdata 
6. function 
7. thread 
8. **tables**
   The table type implements **associative arrays**. An associative array is an array that can be **indexed** not only with numbers, but **also** with strings or any other value of the language, **except** nil. Moreover, tables have no fixed size; you can add as many elements as you want to a table dynamically. Tables are the main (in fact, the only) data structuring mechanism in Lua, and a powerful one. We use tables to represent **ordinary** **arrays**, symbol tables, sets, records, queues, and other data structures, in a simple, uniform, and **efficient** way. Lua uses tables to represent packages as well. When we write `io.read`, we mean "the read entry from the io package". For Lua, that means "index the table io using the string "read" as the key".

    Tables in Lua are neither values nor variables; they are **objects**. You may think of a table as a dynamically allocated object; your program only **manipulates** references (or pointers) to them. There are *no hidden copies* or *creation* of new tables behind the scenes. Moreover, **you do not have to declare** a table in Lua; in fact, there is no way to declare one. You create tables by means of a **constructor expression**, which in its simplest form is written as `{}`:
    ```Lua
        a = {}     -- create a table and store its reference in `a'
        k = "x"
        a[k] = 10        -- new entry, with key="x" and value=10
        a[20] = "great"  -- new entry, with key=20 and value="great"
        print(a["x"])    --> 10
        k = 20
        print(a[k])      --> "great"
        a["x"] = a["x"] + 1     -- increments entry "x"
        print(a["x"])    --> 11
    ```
    A table is always **anonymous**. There is no fixed relationship between a variable that holds a table and the table itself:
    ```Lua
        a = {}
        a["x"] = 10
        b = a      -- `b' refers to the same table as `a'
        print(b["x"])  --> 10
        b["x"] = 20
        print(a["x"])  --> 20
        a = nil    -- now only `b' still refers to the table
        b = nil    -- now there are no references left to the table
    ```

    When a program has no references to a table left, Lua memory management will eventually **delete** the table and **reuse** its memory.
    Each table may store values with different types of indices and it **grows** as it needs to accommodate new entries:

    ```Lua 
    a = {}     -- empty table
    -- create 1000 new entries
    for i=1,1000 do a[i] = i*2 end
    print(a[9])    --> 18
    a["x"] = 10
    print(a["x"])  --> 10
    print(a["y"])  --> nil
    ```

    Notice the last line: Like global variables, table fields **evaluate to** `nil` if they are not initialized. Also like global variables, you can assign nil to a table field to delete it. That is not a coincidence: Lua stores global variables in ordinary tables.
    To represent records, you use the field name as an index. Lua supports this representation by providing `a.name` as syntactic sugar for `a["name"]`. So, we could write the last lines of the previous example in a cleanlier manner as
    ```
        a.x = 10                    -- same as a["x"] = 10
        print(a.x)                  -- same as print(a["x"])
        print(a.y)                  -- same as print(a["y"])
    ```
    For Lua, the two forms are equivalent and can be intermixed freely; but for a human reader, each form may signal a different intention.
    > A common mistake is to confuse `a.x` with `a[x]`. The first form represents a["x"], that is, a table **indexed** by the string "x". The second form is a table indexed by the **value** of the variable x. See the difference:

    ```Lua        
        a = {}
        x = "y"
        a[x] = 10                 -- put 10 in field "y"
        print(a[x])   --> 10      -- value of field "y"
        print(a.x)    --> nil     -- value of field "x" (undefined)
        print(a.y)    --> 10      -- value of field "y"
        
    ```
    To represent a **conventional array**, you simply use a table with **integer keys**. There is *no way* to declare its **size**; you just initialize the elements you need:

    ```Lua
       -- read 10 lines storing them in a table
        a = {}
        for i=1,10 do
        a[i] = io.read()
        end
    ```
    
    When you **iterate over** the elements of the array, the first non-initialized index will result in `nil`; you can use this value as a **sentinel** to represent the *end of the array*. For instance, you could print the lines read in the last example with the following code:

    ```Lua
        -- print the lines
        for i,line in ipairs(a) do
        print(line)
        end
    ```

    The basic Lua library provides `ipairs`, a handy function that allows you to **iterate over** the elements of an array, following the convention that **the array ends** at its **first nil** element.
    Since you can index a table with any value, you can start the indices of an array with any number that pleases you. However, 
    
    > **CONVENTION:** it is customary in Lua to **start arrays with one** (and not with zero, as in C) and the standard libraries stick to this convention.

    Because we can index a table with any type, when indexing a table we have the same subtleties that arise in equality. Although we can index a table both with the number `0` and with the string `"0"`, these two values are different (according to equality) and therefore **denote different positions in a table**. By the same token, the strings "+1", "01", and "1" all denote different positions. When in doubt about the actual types of your indices, use an explicit conversion to be sure:

    ```Lua
        i = 10; j = "10"; k = "+10"
        a = {}
        a[i] = "one value"
        a[j] = "another value"
        a[k] = "yet another value"
        print(a[j])            --> another value
        print(a[k])            --> yet another value
        print(a[tonumber(j)])  --> one value
        print(a[tonumber(k)])  --> one value
    ```
    You can introduce subtle bugs in your program if you do not pay attention to this point.
    
### Type function
The type function gives the type name of a given value:

```Lua 
    print(type("Hello world"))  --> string
    print(type(10.4*3))         --> number
    print(type(print))          --> function
    print(type(type))           --> function
    print(type(true))           --> boolean
    print(type(nil))            --> nil
    print(type(type(X)))        --> string -> no matter the value of x, the result of type is always a string   
```
 Moreover:
 * Variables have **no** predefined types
 * **nil** can be used  to differentiate a **normal** return value from an **exceptional** condition.

## Repeat

As the name implies, a repeat-until statement repeats its body until its condition is true. The test is done after the body, so the body is always executed at least once.

    ```LUA
    -- print the first non-empty line
    repeat
      line = io.read()
    until line ~= ""
    print(line)
    ```

## Errors
We can write

```Lua
    print "enter a number:"
    n = io.read("*number")
    if not n then error("invalid input") end
```
Such combination of `if not ... then error end` is so common that Lua has a built-in function just for that job, called `assert`:

```Lua
    print "enter a number:"
    n = assert(io.read("*number"), "invalid input")
```
The `assert` function checks whether its first argument is not `false` and simply returns that argument; if the argument is false (that is, false or nil), assert raises an error. Its second argument, the message, is **optional**
> When a function finds an unexpected situation (an exception), it can assume two basic behaviors: It can return an error code (typically nil) or it can raise an error, calling the error function.

## Error Handling and Exceptions

To handle errors in Lua, we should use the `pcall` function (protected call) to encapsulate our code.

```Lua
    function foo ()
        ...
      if unexpected_condition then error() end
        ...
      print(a[i])    -- potential error: `a' may not be a table
        ...
    end
```
Then, you call foo with pcall:
```Lua
    if pcall(foo) then
      -- no errors while running `foo'
      ...
    else
      -- `foo' raised an error: take appropriate actions
      ...
    end
```

# Professor's snippets 

Here below is reported a colelction of the example we have seen among the course 

* **First snippet:** *string and their concatenation*
```Lua
    name = " Jhon"  -- leave a space before the name
    print("Hello" .. name) --> Hello Jhon
    -- testing 
    test1 = string.byte("H") 
    print(test1) --> 72
    test2 = string.char(72)
    print(test2) --> H
```

* **Second snippet:** *functions and their use *
```Lua
    -- function definition
    -- local and global variables 
    -- inbuilt library usage

    -- function definition
    function sum(a,b)
        local test = "Flexible automation"
        print(test)
        return math.ceil(a+b)
    end 

    -- test the function
    va1=55
    va2=555.666
    result = sum(va1,va2) --> 611
    print(result) --> nill -- indeed result is not initialised 
```

* **third snippet:** *comparison between min and max value *
  
```Lua
function minmax(a,b)
    if a<b then
        return a,b,20
    else 
        return b,a,50
    end
end

var1=3 
var2=5
minval,maxval,arv = minmax(var1,var2)
-- printing values
print('Min: ' .. minval) --> Min: 3
print('Max: ' .. maxval) --> Max: 4
print('Arv: ' .. arb)    --> Val: 20

```
* **Fourth snippet** *Empty table population*

```Lua
-- Table
-- diagonal matrix: Identity Matrix 
-- #A no. of elements in A

A ={{0,0,0}, {0,0,0}, {0,0,0}}
for i=1, #A, 1 do
    for j=1,#A[i], 1 do
        if i==j then 
        A[i][j]= 1
        end
        print(A[i][j])
    end
end

-- Empty table population

A = {} -- empty table declaration
for i=1,3,1 do
    A[i]= {} -- empty table initialization
    for j=1,3,1 do
    if i=j then 
        A[i][j] = 1 -- value assignment
    else 
        A[i][j] = 0 -- value assignment 
    end
end 
```

* **Fifth snippet**: *arrays and struct*

```Lua
-- Power of table

-- simple array
table0= {10,20,30,47}
table.insert(table0,55) -- adding an entry
table,sort(table0) -- sorting the table
for i=1, #table0, 1 do
    print(table0[i])
end

--KeyValue pairs struct
point = {
    x =18,
    y=45
}
print("x: " .. point.x .. " y: " .. point.y )

--KeyValue pairs struct
table1 = {
["value1"] = 123,
["value2"] = 125.666,
["value3"] = "FA"
["value4"] = true
}
print(#table1)
print(table1["value2"])
print(table1.value4))
```