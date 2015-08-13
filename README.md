# Coding and version control guildlines
Please use this as reference to all guildlines and best practices to follow while coding in C# and JavaScript. It also list the best practices to follow with version control

### C# 
Coding Guidelines  
1. All classes, methods, constants, properties and public fields names to follow Pascal casing  
2. All private variables and fields names have to follow Camal casing  
3. Every file should have one class definition  
4. The file name and class name should match  
5. Always add access providers – private, public and protected – to all classes, properties, methods and fields. C# allows you to skip access provider if it is private. But as per our guidelines, always add private access providers   
6. The var keyword should only be used if the type of the field is directly visible on the right.    
                      var movies = new List<Movies>();  is allowed since the type is visible on right  
                      var movies = GetMovies (); is not allowed since type is not visible on the right  
7. Every closing brace bracket should be followed by a single blank line unless it is followed by another closing brace bracket.  
8. Every method should be responsible to do just one action. If a method is doing more than one operation, split them into multiple methods. The method name should be descriptive enough to clearly tell you what function it performs. Even if that requires you to write a very long name for the method.  
9. In a class, define first the private fields, followed by constructor, followed by any properties, followed by public methods and then private ones  
10. Design classes based on Single Responsibility Pattern. Name the class that describes its responsibility clearly.  
11. Use Linq instead of looping wherever possible  
12. Code should properly indented  
13. Use proper exception handling where ever necessary. If empty catch block has to be use to swallow an exception then proper comments should be provided to indicate the reason for it.  
14. A comment is always is written in following format “// KB: …..”. Add a single space after the “//” and the initials of the developer adding the comment should be added followed by his comments  
15. Reuse code as much as you can  
