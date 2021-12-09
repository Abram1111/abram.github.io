# const uses in c++
Constant is something that doesn't change. In C++ we use the keyword const to make program elements constant. const keyword can be used in many contexts in a C++ program. It can be used with:

## 1.	Variables
## 2.	Pointers
## 3.	Function arguments and return types
## 4.	Class data member
## 5.	Class member function 
## 6.	Objects

# 1) Constant Variables in C++
If you make any variable as constant, using const keyword, you cannot change its value. Also, the constant variables must be initialized while they are declared.

       int main
    {

    const int i = 10;
    const int j = i + 10;     // works fine
    i++;    // this leads to Compile time error  
    
     }

In the above code we have made i as constant, hence if we try to change its value, we will get compile time error. Though we can use it for substitution for other variables.


## 2) Pointers with const keyword in C++

Pointers can be declared using const keyword too. When we use const with pointers, we can do it in two ways, either we can apply const to what the pointer is pointing to, or we can make the pointer itself a constant.

Pointer to a const variable

This means that the pointer is pointing to a const variable.


    const int* u;

Here, u is a pointer that can point to a const int type variable. We can also write it like,

     char const* v;


still it has the same meaning. In this case also, v is a pointer to an char which is of const type.

Pointers to a const variable is very useful, as this can be used to make any string or array immutable(i.e they cannot be changed).

## const Pointer

To make a pointer constant, we have to put the const keyword to the right of the *.

     int x = 1;
     int* const w = &x;

Here, w is a pointer, which is const, that points to an int. Now we can't change the pointer, which means it will always point to the variable x but can change the value that it points to, by changing the value of x.

The constant pointer to a variable is useful where you want a storage that can be changed in value but not moved in memory. Because the pointer will always point to the same memory location, because it is defined with const keyword, but the value at that memory location can be changed.

## NOTE:
We can also have a const pointer pointing to a const variable.

   

     const int* const x;

    

# 3) const Function Arguments and Return types

We can make the return type or arguments of a function as const. Then we cannot change any of them.

    void f(const int i)

    {

    i++;    // error
    
    }

    const int g()

    { 

    return 1;
    
    }

## Some Important points to Remember

1. For built in datatypes, returning a const or non-const value, doesn't make any difference.

	     const int h()
   
               {
	
                 return 1;
      	
               }
	
              int main()
	
               {
 	
                  const int j = h();
	
                   int k = h();
	
                 }

	Both j and k will be assigned the value 1. No error will occur.
   
2.	For user defined datatypes, returning const, will prevent its modification.

3.	Temporary objects created while program execution are always of const type.

4.	If a function has a non-const parameter, it cannot be passed a const argument while making a call.

	    void t(int*) 
   
	      { 
   
	    // function logic
       
            }

If we pass a const int* argument to the function t, it will give error.

5.	But, a function which has a const type parameter, can be passed a const type argument as well as a non-const argument.

	    void g(const int*) 
   
	   {
   
	    // function logic
       
           }

This function can have a int* as well as const int* type argument.

________________________________________

# 4) Defining Class Data members as const

These are data variables in class which are defined using const keyword. They are not initialized during declaration. Their initialization is done in the constructor.

        class Test
            {
    
    const int i;
    public:
    
    Test(int x):i(x)
    {
        cout << "\ni value set: " << i;
    }
    
       };

        int main()
      {

    Test t(10);
    Test s(20);
         }

In this program, i is a constant data member, in every object its independent copy will be present, hence it is initialized with each object using the constructor. And once initialized, its value cannot be changed. The above way of initializing a class member is known as Initializer List in C++.

________________________________________
# 5) Defining Class Object as const

When an object is declared or created using the const keyword, its data members can never be changed, during the object's lifetime.

Syntax:

       const class_name object;

For example, if in the class Test defined above, we want to define a constant object, we can do it like:

      const Test r(30);

# 6) Defining Class's Member function as const

A const member functions never modifies data members in an object.

Syntax:

        return_type function_name() const;



_______________________________________________________________________________________________________________________________________________________
# The use of & in C
## •	Logical-and
      if ( ( a>1 ) && (b<0) ) 
## •	Bitwise-and
         x = a&b; Corresponding bits are and'ed (e.g. 0&1 -> 0)
## •	Bitwise-and-assign
       x &= y; Means the same as: x = x&y;
## •	Address-of operator
       p = &x; Read: Assign to p (a pointer) the address of x.
## •	The additional use of & (in parameters) in C++
C++ uses a type of variable called a "reference" variable (or simply a "reference") which is not available in C (although the same effect can be achieved using pointers). References, pointers and addresses are closely related concepts. Addresses are addresses in computer memory (typically the address in memory where the value of some variable is stored), e.g. (in hexadecimal) 0xAB32C2. Pointers are variables which hold addresses, and so "point to" memory locations (and thus to the values of variables). Conceptually, reference variables are basically pointers by another name (but may not be instantiated as such by the compiler).

It is possible to declare a reference within a function, like other variables, e.g.

       void main(void) 
     { 

       int i; 
       int& r = i; 
          ...
 
      }

but this is pointless, since the use of the reference is equivalent to the use of the variable it references.
References are designed to be used as parameters (arguments) to functions, e.g.

     void f(int& r);


     void main(void) 
     {

     int i=3;
      f(i); 
       printf("%d",i); 
   
     }


       void f(int& r) 

      { 

          r = 2*r; 

          }

This program prints "6" (2*r doubles the value of the variable referenced by r, namely, i).
We could do the same in C by declaring f() as void f(int *r), in which case r is a pointer to an int, then calling f() with argument &i (address-of i), and using de-referencing of r within f(), but clearly C++ provides a more elegant way of passing values to functions (by reference) and returning (perhaps multiple) values from functions (without use of a return statement).


