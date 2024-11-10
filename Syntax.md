# SYNTEX

```cpp

// Single Line Comment 

/*
* multiline 
*comment
*/
```
## Varaible 
```cpp

//static variale [scope with in the file ]                      acess variablename
// local variable  
    // local variable [scope { within block}]                   access variablename
    //global variable [scope any portion of program ]           access variablename or ::(scope resolution)

//intance variable [with in the oject and its visibilty]        access object :: or dereference  (->) variablename

auto            lifetime(functionblock)         visiiblity(local)       initialization( garbagevalue)
extern          lifetime(whole program)         visiiblity(global)      initialization( zero)
static          lifetime(whole program)         visiiblity(local)       initialization( zero)
Register        lifetime(functionblock)         visiiblity(local)       initialization( garbagevalue)
mutable         lifetime(class)                 visiiblity(local)       initialization( garbagevalue)
Thread_local    lifetime(whole thread)          visiiblity(local)       initialization( garbagevalue)




type variable_name;
type variable_name1, variable_name 2 ;
//valid
int x; 
int _yz;
float z400; 
//invalid 
int 89;//All the variable names must begin with a letter of the alphabet or an underscore(_)
float a b;//The name of the variable contains letters, digits, and underscores.
float char; //c++ keywords can not be used.
```

## CONSTANTS
    1. const Keyword (compile or run time)
    2. constexpr ( compile time)
    3. #define (Macro constant - preprocessor time)

``` cpp
const  DATATYPE variable_name = value ;  // const 
DATATYPE const variable_name = value ;    // const 
constexpr DATATYPE variable_name = value ; // constexpr
DATATYPE constexpr variable_name = value ;// constexpr
#define name value ; // define
```

## Static 
1. variable as static  // scope with in the block or class not object
2. functions as static  // scope with in file or with in the class not objects
3. object as static    // scope whole program - destrctor will after main() ends.
```cpp
static int a   = 10;   
static void func();
class a{
    static int b ; //initialize outside the class
    static void func2();
}
//initialization and decleartion
int a::b = 20; //classname::variable
void a::func2() // classname::funtionname

//calling 
a::b;
a::func2();
// object as static
int main()
{
    static a static_a; //static object scope is constructor of a -> end main -> destructor of a.
}
```
## DataTypes

### Primary 
```cpp 
    int // if not provided unsigned or signed  it act as signed.
        unsigned int
            unsigned short int
            unsigned long int
            unsigned long long int 
        signed int 
            signed short int 
            signed long int
            signed long long int 
    floating point 
        double 
        float 
        long double 
    
    char
        signed 
        unsigned
```
> [!NOTE]
Size is variosu based on compiler to compiler so  use header <limits.h> 
example: CHAR_MAX, SCHAR_MAX INT_MAX etc

## Literals

```cpp
255, 0377, 0xff, 0b10110    // Integers (decimal no prefix, octal represented by 0, hex ( X or x), Binary (b or B))
2147483647L, 0x7fffffffl    // Long (32-bit) integers
2147483647U, 2147483647u    // Usigned int (U or u)
2147483647LL , 2147483647ll // Long long int (ll or LL)
123.0, 1.23e2 , 3.14f       // double (real) numbers,float
'A', u8'A'                  // char
L'A',u'A', U'A'              //wchart , char16_t, char32_t
"string", u8"string"        //const char* , const char8_t*
L"string",u"string", U"string"//const wchart* , const char16_t*, const char32_t*

"string"s, u8"string"s        //std::string  , std::u8string
L"string"s,u"string"s, U"string"s//std::wstring , std::u16string, std::u32string
R"("Hello \ world")"s;      // Raw std::string from const char*
'a', '\141', '\x61'         // Character (literal, octal, hex)
'\n', '\\', '\'', '\"'      // Newline, backslash, single quote, double quote
"string\n"                  // Array of characters ending with newline and \0
"hello" "world"             // Concatenated strings
true, false                 // bool constants 1 and 0
nullptr                     // Pointer type with the address of 0
```
## Derived Data Type
### Function
```cpp
return funname (argument);
```
### Array 
 datatype arrayname[size_of_array];

### Pointers
datatype *var_name;

### Reference 

datatype &varname = variable;

### class 
``` cpp
class class_name
{
    access_specifier:
    member variable;
    member functions;
};
```
### struct
``` cpp
struct struct_name
{
    access_specifier:
    member variable;
    member functions;
};
//Create Instance
struct_name obj_name;/* Access array member */ obj_name.membervariable;
//array of structure :
 struct Point arr[10];/* Access array member */arr[0].member_variable = 10;
//struct pointer
struct point * p2 = struct_name; /* Access array member */arr[0]->member_variable = 10;
```
### Union
``` cpp
union union_name
{
    member variables; //size of union is maximum size of variable used.
};
//Create Instance
union_name obj_name;
obj_name.membervariable;
```

### enum
``` cpp
enum enum_name
{
    variables= value; //size of union is maximum size of variable used.
};
```

### typedef

```cpp
typedef unsigned int UINT;
```

## Data Type COnversion
### implict conversion 
bool -> char -> short int -> int -> unsigned int -> long -> unsigned -> long long -> float -> double -> long double

### Explict conversion 
```cpp
float a =10.3;
int b = (int)a+20; // a is converted to int value .
```
#### using cast operators 
static_cast<T>(x)           // Converts x to a T, not checked , it compile time
dynamic_cast<T>(x)          // Converts x to a T, checked at run time( using pointer conversion from one class to another)
reinterpret_cast< T>(x)     // Interpret bits of x as a T ( using differnt pointer conversion)
const_cast< T>(x)           // Converts x to same type T but not const ( convert oconst to non-const)

## Expressions

Operators are grouped by precedence, highest first. Unary operators and assignment evaluate right to left. All
others are left to right. Precedence does not affect order of evaluation, which is undefined. There are no run time
checks for arrays out of bounds, invalid pointers, etc.

```cpp
//left to right
T::X                        // Name X defined in class T
N::X                        // Name X defined in namespace N
::X                         // Global name X
f(x,y)                      // Call to function f with arguments x and y
T(x,y)                      // Object of class T initialized with x and y
a[i]                        // i'th element of array a
//right to left
t.x                         // Member x of struct or class t
p-> x                       // Member x of struct or class pointed to by p
x++                         // Add 1 to x, evaluates to original x (postfix)
x--                         // Subtract 1 from x, evaluates to original x
typeid(x)                   // Type of x
typeid(T)                   // Equals typeid(x) if x is a T
dynamic_cast< T>(x)         // Converts x to a T, checked at run time.
static_cast< T>(x)          // Converts x to a T, not checked
reinterpret_cast< T>(x)     // Interpret bits of x as a T
const_cast< T>(x)           // Converts x to same type T but not const

sizeof x                    // Number of bytes used to represent object x
sizeof(T)                   // Number of bytes to represent type T
++x                         // Add 1 to x, evaluates to new value (prefix)
--x                         // Subtract 1 from x, evaluates to new value
~x                          // Bitwise complement of x
!x                          // true if x is 0, else false (1 or 0 in C)
-x                          // Unary minus
+x                          // Unary plus (default)
&x                          // Address of x
*p                          // Contents of address p (*&x equals x)
new T                       // Address of newly allocated T object
new T(x, y)                 // Address of a T initialized with x, y
new T[x]                    // Address of allocated n-element array of T
delete p                    // Destroy and free object at address p
delete[] p                  // Destroy and free array of objects at p
(T) x                       // Convert x to T (obsolete, use .._cast<T>(x))

//Left to right 
x * y                       // Multiply
x / y                       // Divide (integers round toward 0)
x % y                       // Modulo (result has sign of x)

x + y                       // Add, or \&x[y]
x - y                       // Subtract, or number of elements from *x to *y
x << y                      // x shifted y bits to left (x * pow(2, y))
x >> y                      // x shifted y bits to right (x / pow(2, y))

x < y                       // Less than
x <= y                      // Less than or equal to
x > y                       // Greater than
x >= y                      // Greater than or equal to

x & y                       // Bitwise and (3 & 6 is 2)
x ^ y                       // Bitwise exclusive or (3 ^ 6 is 5)
x | y                       // Bitwise or (3 | 6 is 7)
x && y                      // x and then y (evaluates y only if x (not 0))
x || y                      // x or else y (evaluates y only if x is false (0))
// right to left
x = y                       // Assign y to x, returns new value of x
x += y                      // x = x + y, also -= *= /= <<= >>= &= |= ^=
x ? y : z                   // y if x is true (nonzero), else z
throw x                     // Throw exception, aborts if not caught
x , y                       // evaluates x and y, returns y (seldom used)
```
## Streams
```cpp
#include<iostream>           //cin, cout,cerr
#include<iomanip>            // setw,setprecision
#include<fstream>            // file access
#include<bits/stdc++>        // for all

```
### input Streams 
Key board to program (cin)
cin done using >>(extraction operator ) (istream)
```cpp
cin.get()               //read single char
cin.getline()           //read line of text
cin.ignore()            //ignore specified no of char 
cin.read()
```

### output stream 
program to Screen (cout, cerr,clog)
cerr -> unbuffered data, it never stored. 

```cpp
cout.write(char *str, int n)                //read single char
cout.put(char &ch)                          //read line of text
cout.precision(int n)                       //ignore specified no of char 
```


## Statements

```cpp
x=y;                        // Every expression is a statement
int x;                      // Declarations are statements
;                           // Empty statement
{                           // A block is a single statement
    int x;                  // Scope of x is from declaration to end of block
}
if (x) a;                   // If x is true (not 0), evaluate a
else if (y) b;              // If not x and y (optional, may be repeated)
else c;                     // If not x and not y (optional)

while (x) a;                // Repeat 0 or more times while x is true

for (x; y; z) a;            // Equivalent to: x; while(y) {a; z;}

for (x : y) a;              // Range-based for loop e.g.
                            // for (auto& x in someList) x.y();

do {a;} while (x);          // Equivalent to: a; while(x) a;

switch (x) {                // x must be int
    case X1: a;             // If x == X1 (must be a const), jump here
    case X2: b;             // Else if x == X2, jump here
    default: c;             // Else jump here (optional)
}
break;                      // Jump out of while, do, or for loop, or switch
continue;                   // Jump to bottom of while, do, or for loop
return x;                   // Return x from function to caller
try { a; }
catch (T t) { b; }          // If a throws a T, then jump here
catch (...) { c; }          // If a throws something else, jump here
```

### range Loop
```cpp
#include <iostream>
#include <map>
#include <string>
#include <vector>
using namespace std;

// Driver
int main()
{
    // Iterating over whole array
    vector<int> v = { 0, 1, 2, 3, 4, 5 };for (auto i : v)cout << i << ' ';cout << '\n';

    // the initializer may be a braced-init-list
    for (int n : { 0, 1, 2, 3, 4, 5 })cout << n << ' ';cout << '\n';

    // Iterating over array
    int a[] = { 0, 1, 2, 3, 4, 5 };for (int n : a)cout << n << ' ';cout << '\n';

    // Just running a loop for every array
    for (int n : a)cout << "In loop" << ' ';cout << '\n';

    // Printing string characters
    string str = "Geeks";for (char c : str)cout << c << ' ';cout << '\n';

    // Printing keys and values of a map
    map<int, int> MAP({ { 1, 1 }, { 2, 2 }, { 3, 3 } });for (auto i : MAP)cout << '{' << i.first << ", " << i.second << "}\n";
}
```

## Pointer
```cpp
datatype var_name;
datatype *pointer_name; //pointer decleration
pointer_name = & var_name; //pointer assignment
```
### dangling pointer 
### wild pointer 
### null pointer 
 NULL  return 0  as interger using char * 
 nullptr return bool ( false)

### void pointer
### this pointer
```cpp
    non static function has hidden pointer 
    ex:
    void func()
    {
        int x; // can access by x or this->x.
    } 

```


## array
```cpp
int arr_name[20];
int arr[row];

//initialization
int arr_name[5] ={1,2,3,4,5};
arr_name[0] = 20;

//pointer to an array
int *ptr = arr_name;
*(arr_name+1) = 25;

//pointers of array 
 int (*ptr)[5] = &arr_name;

// Declaring 2D array
int arr[row][column];
arr[i][j] = *(*(arr+i)+j);
// Declaring 3D array
int arr[Depth][row][column];
```