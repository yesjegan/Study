# Different Functions in c++

> [!NOTE] 
* returntype function_name (param_type param_name,param_type param_name);
* inline returntype function_name (param_type param_name,param_type param_name);


```cpp
//Funtion
int swab( int a, int b);    /*pass by value */      swab(a,b)   /*call by value*/
int swab( int* a, int* b);  /*pass by pointer */    swab(&a,&b)   /*call by adress*/
int swab( int& a, int& b);  /*pass by value */      swab(a,b)   /*call by refernce*/

int swab ( int a, int b = 20); //default argument works right to left int a =20, int b  syntax issue.

//Function POinter
datatype (*fun_name) 
```
 ## function Over load issue
 ```cpp
 int sum(int x, int y, int z = 0, int w = 0)
 int sum(int x, int y)  // sum(10, 15, 25, 30) ans sum(19,20) dont know which one should call

```cpp
 ## recursive fucntion

 //function call its own function
 int sum(int a)
 {
    if(a==0)
    {
        return 0;
    }
    return res = res+ sum(a--); 
 }
 ```

 ## macro vs inline 
 Macro error check wont do . 


 ## Lamda 
 ``` cpp
 [capture clause] (parameters) -> return-type   
{    
   definitie van methode    
}

Capture by reference 
Capture by value 
Capture by both (mixed capture)
Syntax used for capturing variables : 
      [&] : capture all external variables by reference 
      [=] : capture all external variables by value 
      [a, &b] : capture a by value and b by reference
```

## passing array to function

return_type function_name (datatype *array_name){}
return_type function_name (datatype array_name[]){}
return_type function_name (datatype array_name[size of array]){}

return_type functionname (data_type (&array)[size] //no array decay
    int arr[] = { 1, 2, 3, 4, 5 };
    int n = 5;
    modifyArray(arr);
void modifyArray(int (&arr)[5])

> [!NOTE] 
 Array will be treated as a pointer in the passed function no matter what method we use. As the array are passed as pointers, they will loose the information about its size leading to a phenomenon named as Array Decay.


## passing string to a function 
 ```cpp
    string s = "GeeksforGeeks";
    print_string(s);void print_string(string s);
 ```
