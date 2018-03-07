 # Polymorphism & Composition Homework - Quiz
 # Polymorphism

  1. What does the ___word___ 'polymorphism' mean?

  Greek word meaning:

  Poly = many
  Morphism = shaped

  In O-O, it means the ability for one object to take on many different forms.

  2. What does it mean when we apply polymorphism to OO design? Give a simple Java example.

  The ability to decide which methods to use, based on the type of the Object.

  e.g. It allows us to treat a derived class member just like it's parent class's members.

  If we create an instance of class Dog, where class Dog either:

  (1) Is a child class of parent class Pet, where class Dog inherits all methods of class Pet, but also has extra Dog methods, and may also override some of the generic Pet methods.

  -OR-

  (2) Has a common interface, e.g. interface ITalk (where interface ITalk is a 'contract' that says each class, e.g. class Dog, that 'implements' this interface must have its own versions of methods that have been declared in the common interface ITalk).

  Then polymorphism is the ability to store an instance of a sub-type in a data structure of it's parent type (or interface type), and cast it back into a sub-type at a later stage, so that the program can call the different methods (versions of methods) belonging to the different types/sub-types on the same Object at different points in the program:

  e.g.
  (a) Create an instance of class Dog.
  (b) Assign the class Dog instance to a more generic class Pet object, e.g. store it in an ArrayList of Pet objects.
      - So that we can store many different sub-types of Pet, e.g. Dog, Cat in the same ArrayList.
      - And we can invoke the generic methods.
  (b) Cast an element in the Pet ArrayList back into its actual sub-type, i.e. Dog.
      - So that we can then invoke the specific Dog methods.

  i.e.
  Dog dog = new Dog();                          // Create an instance of Dog
  ArrayList<Pet> pets = new ArrayList<>();      // Create a new array 'pets' to store Pet objects
  pets.add(dog);                                // Add the Dog instance to the 'pets' array

  for (Pet pet : pets){
    if (pet instanceof Dog){                    // If 'pet' is an instance of Dog
      Dog dog = (Dog) pet;                      // Cast 'pet' back into sub-type Dog
    }
  }

  3. What can we use to implement polymorphism in Java?

  (1) Interfaces:
  We can declare an interface, e.g. ITalk, which is 'implemented' by several sub-type classes, e.g. Dog, Cat.  
  Within each sub-type class, they will have their own version of methods that have been declared in ITalk (polymorphism).

  (2) Inheritance & Casting:
  Create instances of sub-types --> store as the parent-type --> cast back to sub-type again.

  4. How many 'forms' can an object take when using polymorphism?

  As many 'forms' as we have parent/grand-parent classes for that object, and/or interfaces that have been applied to the class of that object.

  5. Give an example of when you could use polymorphism.

  (1) A Pet class could have a generic makeNoise() method, and the Dog and Cat classes could override the makeNoise() method.

  (2) The Dog and Cat classes could implement their own versions of makeNoise() methods, which have been declared in the ITalk interface.

  In both cases, a generic Pet could be made to behave like a Dog or a Cat.


  # Composition

  6. What do we mean by 'composition' in reference to object-oriented programming?

  It is a way to share behaviour across a subset of classes.

  If there are common methods (behaviours) that are required by a sub-set of sub-types (child classes), then composition enables those classes to have polymorphic behaviours by declaring a common interface that each of those classes 'implements'.

  i.e. each of those sub-type classes contain instances of the common interface, and the common interface declares the additional methods that must be defined in each of those sub-type classes.

  Composition is an alternative to inheritance and enables a class to have different method's associated with it.

  Composition can be used in addition to inheritance, or instead of inheritance entirely.


  7. When would you use composition? Provide a simple example in Java.

  class Dog extends Pet implements ITalk {...}
  class Cat extends Pet implements ITalk {...}

  The above class declarations use composition to add common methods (behaviours) declared in ITalk to both the Dog and the Cat class.


  8. What is/are the advantage(s) of using composition?

  Allows a class to be polymorphic, and is the closest we get to multiple inheritance in Java and the ability for an instance of an object to take on many forms.  Java does not support multiple inheritance.

  Composition is now favoured over inheritance by O-O experts.

  9. What happens to the behaviours when the object composed of them is destroyed?

  The behaviours are also destroyed.

  This is because the object owns it's instance of the interface (behaviours), rather than just uses the interface - so if the object is destroyed, then so will it's instance of the interface (i.e. the behaviours) be destroyed.
