# string in c++

## c++ style
```cpp
string str = ("c++");
string str = "c++";
string str("c++");
string str;str = "c++";

string str(5,'j');  // o/p-> jjjjj 
```
### string functions
```cpp
length(),swap(),size(),resize(),find(),push_back(),pop_back(),clear(),
strcmp(),strncpy(),strrchr(),strcat(),find(),replace(),substr(),compare(),erase(),shrink_to_fit()

length() or size()          //lenght of string 
at()                        //individual char using array
+  or append()              //append 
== or compare()             //comparison
substr()                    // extract sub string  from string 
find()                      //search
replace() insert(), erase() // modfiy 
c_str()                     //c-style string from std::string
```
### string Iterator functions
```cpp
begin(),end(),rfind(),rbegin(),rend(),cbegin(),cend(),crbegin(),crend().
```

## c style 
```cpp
char e[] = "c-style";
char e[] = {'a','b','c','d', '\0'};
char *e = "stylechar";
//array of string 
const char* colour[4] = { "Blue", "Red", "Orange", "Yellow" }; // array of string 
char colour[4][10] = { "Blue", "Red", "Orange", "Yellow" }; 
string colour[4] = { "Blue", "Red", "Orange", "Yellow" };
vector<string> colour{ "Blue", "Red", "Orange" };
array<string, 4> colour{ "Blue", "Red", "Orange","Yellow" };
```

## input method
* cin                       //cin>>s; 
* getline(cin,s);           //getline(cin, s);
* stringstream              //stringstream sstram(s); sstram>>temp;

## pointer and string 
```cpp
    string s = "Geeksforgeeks";char *p = &s[0]; while(*p != '\0'){p++;}

```

## tokenize the String 
```cpp
string s("have a nice day");
vector<string> token;
string temp;
stringstream sstream(s); while(getline(sstream,temp,' '))
{
    token.push_back(temp);
}

```
### using strtok
```cpp
char str[] = "Geeks-for-Geeks";
char *token = strtok(str, "-");
```
