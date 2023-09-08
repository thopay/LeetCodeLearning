1. **Modularity**: Design systems in such a way that different parts of the system can be created, modified, and tested independently of others. Modularity allows for easier troubleshooting and flexibility in updating the system in the future.

2. **Decomposition/Abstraction**: Break down the system into simpler, more manageable parts (decomposition). Each part should perform a specific task without knowing the complexities of other parts (abstraction).

3. **SOLID Principles**:
   - *Single Responsibility Principle*: Each module/class should have only one responsibility.
   - *Open-Closed Principle*: Software entities should be open for extension but closed for modification.
   - *Liskov Substitution Principle*: Objects of a superclass should be able to be replaced with objects of a subclass without affecting the correctness of the program.
   - *Interface Segregation Principle*: Multiple, specific interfaces are better than one general-purpose interface.
   - *Dependency Inversion Principle*: High-level modules should not depend on low-level modules. Both should depend on abstractions.

4. **Scalability**: Design should accommodate growth. This includes being able to handle increased loads (load scalability) and being able to add more functionality (functional scalability) without performance degradation.

5. **Performance Optimization**: This involves maximizing or optimizing the speed and efficiency of the system's functionality.

6. **Fail Fast**: The system should halt and report an error condition rather than continuing with inaccurate results.

7. **Loose Coupling**: Dependencies between different modules or components should be minimized. This results in a more flexible and maintainable system.

8. **High Cohesion**: Elements within a module/component should share functionality as much as possible.

9. **Security**: Keep security in mind from the start of the design process.

10. **Design Patterns**: Become familiar with common design patterns applicable to the language you're working in. Examples include Singleton, Factory, Observer, and Decorator.

These principles help in creating a robust, scalable, and maintainable system. Do remember that design solutions will vary greatly depending on requirements, business needs, and the problem at hand. So, these principles are more like guiding tools rather than stringent rules.