---
tags:
  - concept
  - python
---
Duck typing in Python is a dynamic typing concept where the suitability of an object for a specific operation is determined by whether it can perform that operation, rather than by its class or type. In other words, "If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck." In Python, you don't need to specify the type of a variable explicitly; you can assign different types to a variable, and the type is determined at runtime based on the value assigned.

```python
lass Duck:  
   def swim_fly(self):  
         print("I am a duck, and I can swim and fly.")  
   
class Goose:  
     def swim_fly(self):  
         print("I am a Goose, and I can swim and fly.")  
   
class Hippo:  
     def walk(self):  
         print("I am a Hippo, and I can walk but can't swim or fly.")  

# Demonstrating Duck Typing
for obj in Duck(), Goose(), Hippo():
    if hasattr(obj, 'swim_fly'):  # Check if the object has the swim_fly method
        obj.swim_fly()
    else:
        print(f"This object cannot swim and fly: {obj}")
```

Duck typing in Python is a dynamic typing concept where the suitability of an object for a specific operation is determined by whether it can perform that operation, rather than by its class or type. In other words, "If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck." In Python, you don't need to specify the type of a variable explicitly; you can assign different types to a variable, and the type is determined at runtime based on the value assigned.