# OOPS-Last minute revision notes✅

**Object oriented programming** enhances the readibility and maintainability of the code.In OOPS the whole code revolves around objects and classes.

# Class
blueprint or template on behalf of which object can be created

# Object
instance of the class

For eg:
class hai=fruits toh object hoga =apple,mango,banana method hoga =eat,wash,cut(these methods are basically the functions)  attribute hoga=taste ,color

**A class can exist without an object, but an object cannot exist without a class.**

# Function prototyping
declaration statement of the function(basically interface of the function)
function prototyping gives the compiler the details about the functions such as the number and types of arguments and the type of return values.

type function-name (arguments);

# Inline functions
inline functions are basically the small functions.function is expanded in line when it is invoked.function call is replaced by function body

inline function_type function name(arguments){
return a*a*a;
}

# Default arguments
assigns a defualt value to the function parameter which does not have a matching argument
also if one value is needed to be fixed

function can have default arguments from trailing

int mul(int i,int j=5,int k=6); **---true**
int mul(int i=5,int j);  **--false**
int mul(int i=5,int j,int k=10); **--false**
int mul(int i=5,int j=6,int k=8); **--true**


