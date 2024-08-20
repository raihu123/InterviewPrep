### What Are Cross-Cutting Concerns?
**Cross-cutting concerns** are aspects of your application that affect multiple components but aren't core to the main functionality, like logging, security, and transaction management.

**Easy to Remember**: Think of cross-cutting concerns as "side tasks" that apply everywhere but aren’t the main job.

### How Do You Implement Cross-Cutting Concerns in a Web Application?
Use **AOP** (Aspect-Oriented Programming), **filters**, **interceptors**, or **middleware** to handle these concerns across your application without cluttering the core logic.

**Easy to Remember**: AOP for Spring, Filters or Interceptors for pre/post processing, Middleware for centralized handling.

### If You Would Want to Log Every Request to a Web Application, What Are the Options You Can Think Of?
1. **AOP**: Aspect for logging.
2. **Filters**: Log before/after requests.
3. **Interceptors**: Log during request handling.
4. **Middleware**: Centralized logging for all requests.

**Easy to Remember**: Use "AIM-F" - **AOP, Interceptor, Middleware, Filter**.

### If You Would Want to Track Performance of Every Request, What Options Can You Think Of?
1. **AOP**: Measure and log execution time.
2. **Filters**: Track start and end times.
3. **Interceptors**: Measure time taken to process.
4. **Performance Tools**: Use monitoring tools.

**Easy to Remember**: Think "AIP-T" - **AOP, Interceptor, Performance Tools**.

### What is an Aspect and Pointcut in AOP?
- **Aspect**: Modular code for cross-cutting concerns.
- **Pointcut**: Defines where in your code the Aspect applies.

**Easy to Remember**: **Aspect** is the "what" (concern), and **Pointcut** is the "where" (location).

### What Are the Different Types of AOP Advices?
1. **Before Advice**: Runs before the method.
2. **After (Finally) Advice**: Runs after, no matter what.
3. **After Returning Advice**: Runs after success.
4. **After Throwing Advice**: Runs after an exception.
5. **Around Advice**: Wraps around the method.

**Easy to Remember**: "Before, After, After Success, After Exception, Around."

### What is Weaving?
**Weaving** is the process of applying aspects to your code at various stages: compile-time, load-time, or runtime.

**Easy to Remember**: Weaving is like sewing the cross-cutting concerns into your code.

### Compare Spring AOP vs AspectJ
- **Spring AOP**: Runtime weaving, method-level, proxy-based.
- **AspectJ**: Supports compile, load, runtime weaving, more powerful, requires AspectJ compiler.

**Easy to Remember**: **Spring AOP** = **Simple** (runtime, method-only). **AspectJ** = **Advanced** (all-around).