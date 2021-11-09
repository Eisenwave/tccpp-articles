# What are the different casts in c++

##C-style cast  
?inline
- Used to perform implicit or explicit type conversions between types  
- Prefer using specific cast instead of this one if possible  
- Evaluated at compile-time  

###Example  
```c++
// seatCount is initially int, but we need unsigned int so we convert it
int seatCount = 100;
unsigned int receivedPackedsShort = (unsigned int) seatCount;
```

##static_cast  
?inline
- Used to perform implicit or explicit type conversions between types  
- Evaluated at compile-time  

###Example:  
```c++
// seatCount is initially int, but we need unsigned int, so we convert it
int seatCount = 100;
unsigned int seatCountUnsigned = static_cast<unsigned int>(seatCount);
```

##reinterpret_cast  
?inline
- Used to convert any pointer to any other datatype  
- Evaluated at compile-time  

###Example  
```c++
// Example from converting Vulkan-Hpp object to Vulkan.h (C-style) object
vk::Device device;
VkDevice device_c = reinterpret_cast<VkDevice>(device);
```

##const_cast  
?inline
- Used to convert normal type to const type
- Evaluated at compile-time

###Example  
```c++
// Function to convert int to const int
const int make_const(int a) {
	return const_cast<const int>(a);
}
```

##dynamic_cast  
?inline
- Used to either downcast or upcast a class with atleast one virtual method  
- Evaluated at run-time  

###Example  
```c++
class SuperClass {
public:
	virtual void sayHello();
};
class Derived : public SuperClass {
public:
	virtual void sayHello() override;
};

int main() {
	SuperClass super {};
	Derived* superToDerived = dynamic_cast<Derived*>(&super);
}
```

###Resources  
**[C-style cast](https://en.cppreference.com/w/cpp/language/explicit_cast)**  
**[static_cast](https://en.cppreference.com/w/cpp/language/static_cast)**  
**[reinterpret_cast](https://en.cppreference.com/w/cpp/language/reinterpret_cast)**  
**[const_cast](https://en.cppreference.com/w/cpp/language/const_cast)**  
**[dynamic_cast](https://en.cppreference.com/w/cpp/language/dynamic_cast)**  

**[Microsoft's article on casts](https://docs.microsoft.com/en-us/cpp/cpp/type-conversions-and-type-safety-modern-cpp)**

?creditFooter 379250891838193667
