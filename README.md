# Coding and version control guildlines
Please use this as reference to all guildlines and best practices to follow while coding in C# and JavaScript. It also list the best practices to follow with version control

### C# 
#### Naming Conventions  
###### Static Field Naming Guidelines  
 * DO NOT use Hungarian notation  

Constant Field Naming Guidelines  
 * DO NOT use ALL CAPITALS  
 * DO use PascalCasing for naming constants  

```cs
// incorrect  
private cost string CONST_NAME = “Here is a constant”;  
```  

```cs
// correct  
private cost string ConstName = “Here is a constant”;  
```  

Using Declarations  
 * DO use the features of Visual Studio or Resharper to remove un-necessary using statements and order using statements correctly   

Private Fields  
 * DO use a leading underscore to designate a private field  
```cs  
class MyClass  
{  
  private string _field = null;  
}  
```  

Private Static fields  
 * DO use a double leading underscore to designate a private static field  
```cs  
class MyClass  
{  
  private static string __field = null;  
}  
```  

Usage of “var” keyword  
 * DO NOT use “var” when it is possible to directly infer the type of the variableby looking at RHS
 * Heavy usage of the “var” keyword makes the codebase harder to read. Only use “var” when necessary  
```cs  
// is allowed since the type can be directly inferred from the RHS  
var movies = new List<Movies>();  
  
// is not allowed since the type cannot be directly inferred from the RHS  
var movies = GetMovies();  
```  

Spaces and Tabs  
 * DO use spaces instead of tabs  
 * DO use 4 spaces per indent  
```cs  
class MyClass  
{  
  private static string __field = null;  

  public MyClass()  
  {  
    __field = “hello”;  
  }  
}  
```  

Regions 
 * DO NOT use regions to wrap a single method  
 * DO NOT use regions excessively. Only use them when it adds to the readability and maintainability of the code to group logically related methods. Note if there is a need for a lot of regions in code, it may indicate the class needs to be split up into smaller classes  

Error Handling and Validation  
 * DO leverage the ArgumentValidation class to validate arguments to most public methods, especially Services  
```cs  
class MyService  
{  
  public MyServiceMethod(Order order, int userId)  
  {  
    ArgumentValidation.CheckForNullReference(order, “order”);  
    ArgumentValidation.CheckPositive(userId, “userId”);  

    // method logic  
  }  
}  
```  

 * DO handle error conditions and take appropriate actions sooner rather than later  
```cs  
// Correct  
public MyServiceMethod(int userId)  
{  
  User user = GetUser(userId);  
  
  if (user == null)  
    throw new AppropriateException(“User was not found”);  
  
  // continue with normal method logic  
}  
  
// Incorrect  
public MyServiceMethod(int userId)  
{  
  User user = GetUser(userId);  
  
  if (user != null)  
  {  
    // method logic  
    return;  
  }  
    
  throw new AppropriateException(“User was not found”);  
}  
```  

Constants  
 * DO use constants instead of string literals in code. Constants declared at the top of the page are easier to find and modify, in addition, other classes can reference these constants to avoid string duplication and typo errors. Examples of things that should be constants:  
    *	Messages that the controller displays to the user (for example error messages, success messages etc…)  
    *	C# references to elements that occur in markup, for example element Ids, classes  
    *	Configuration setting keys  
 * The following cases are exceptions:  
    *	View names – Visual Studio will show an error if there is a typo in a view name in code for example return View(“NoExist”) will yield an error  
    *	Log messages that are not referenced by tests – if you are logging a message for development purposes and that message is not referenced by a test, then you can use a string literal  
    *	Validation messages for data annotation attributes that are not referenced elsewhere – if you have validation messages that are not referenced by tests, or other parts of the code, they can utilize string literals. If the message should be referenced by other code (eg a test or to avoid string duplication), it must be a constant 

CSS, HTML and Mobile Screens UI Naming Conventions  
* DO use PascalCasing for HTML element IDs, for example “FeatureBlock”, not “feature-block” not “featureBlock”.  
* DO use a dash to separate words for class names, for example "page-checkin", not “PageCheckin”, not "pageCheckin"  
* DO use descriptive, semantic names that reflect the purpose of the element or class. Avoid using names that are bound to the presentation (for example, location or color related) where possible.  
* DO NOT use abbreviations. Use descriptive names.  
* NOTE: if the name would be greater than 30 characters, abbreviations are acceptable. For example the CSS class applied to the Manage Communication Preferences page should be named "page-manage-comms-pref". The name "page-manage-communication-preferences" is too long, and "page-mcp" is too short and no longer adequately describes the class.  
* DO ensure names are spelt correctly  

General
* All classes, methods, constants, properties and public fields names to follow Pascal casing
* All private variables and fields names have to follow Camal casing  
* Every file should have one class definition  
* The file name and class name should match  
* Always add access providers – private, public and protected – to all classes, properties, methods and fields. C# allows you to skip access provider if it is private. But as per our guidelines, always add private access providers   
* Every closing brace bracket should be followed by a single blank line unless it is followed by another closing brace bracket.  
* Every method should be responsible to do just one action. If a method is doing more than one operation, split them into multiple methods. The method name should be descriptive enough to clearly tell you what function it performs. Even if that requires you to write a very long name for the method.  
* In a class, define first the private fields, followed by constructor, followed by any properties, followed by public methods and then private ones  
* Design classes based on Single Responsibility Pattern. Name the class that describes its responsibility clearly.  
* Use Linq instead of looping wherever possible  
* Code should properly indented  
* Use proper exception handling where ever necessary. If empty catch block has to be use to swallow an exception then proper comments should be provided to indicate the reason for it.  
* A comment is always is written in following format “// KB: …..”. Add a single space after the “//” and the initials of the developer adding the comment should be added followed by his comments  
* Reuse code as much as you can  
