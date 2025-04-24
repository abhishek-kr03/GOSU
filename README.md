**Gosu Language Learning Summary**

---

### 💡 What is Gosu?

Gosu is an open-source, statically-typed programming language that runs on the Java Virtual Machine (JVM). It was created to simplify complex business logic and provide an expressive syntax while maintaining type safety.

---

### 🔍 Why Gosu?

- Built specifically for Guidewire software (PolicyCenter, BillingCenter, ClaimCenter)
- Statically typed with type inference
- Supports enhancements (extension methods)
- Cleaner and more readable syntax than Java
- DSL-friendly for business rule implementation
- Supports named arguments and default parameter values
- Built-in templating support for documents (.gsp files)

---

### ✍️ Core Concepts of Gosu

#### 1. **Type Inference**

```gosu
var name = "Abhishek"  // Gosu infers String type
```

#### 2. **Enhancements** (Extension methods)

```gosu
enhancement MyStringEnhancement : String {
  function toSnakeCase() : String {
    return this.replace(" ", "_").toLowerCase()
  }
}
```

#### 3. **Named Arguments & Default Parameters**

```gosu
function printNames(prefix : String = "> ") {
  for(n in _names) {
    print(prefix + n)
  }
}

c.printNames(:prefix = "* ")
```

#### 4. **Delegates**

```gosu
class MyRunnable implements Runnable {
  delegate _runnable represents Runnable

  property get Impl() : Runnable {
    return _runnable
  }
  property set Impl(r : Runnable) {
    _runnable = r
  }
}

x.Impl = new Runnable() {
  function run() {
    print("Hello, Delegation")
  }
}
x.run()  // Output: Hello, Delegation
```

#### 5. **List Enhancements**

```gosu
enhancement ListEnhancement<T> : List<T> {
  function secondOrNull() : T {
    return this.size > 1 ? this[1] : null
  }
}
```

#### 6. **Date Enhancements**

```gosu
enhancement DateEnhancement : Date {
  function daysUntil(target : Date) : int {
    var millisPerDay = 1000 * 60 * 60 * 24
    return ((target.time - this.time) / millisPerDay) as int
  }
}
```

#### 7. **Blocks and Closures**

```gosu
var names = {"Alice", "Bob", "Charlie"}
var filtered = names.where(\ name -> name.startsWith("A") )
```

#### 8. **Structures and Typelists**
- Used in Guidewire for defining standard values like "State", "ClaimStatus", etc.
- Helps in localization and business logic constraints

#### 9. **Bundles and Transactions**
- Used for managing data persistence in Guidewire
- Example: `Bundle`, `commit()`, `remove()`, `add()`
- Ensures data consistency during DB operations

#### 10. **Gosu Templates (`.gsp` files)**
- Used for generating PDFs, letters, and formatted output
- Contains dynamic expressions and loops
- Looks like HTML + Gosu syntax

#### 11. **Unit Testing in Gosu**

```gosu
uses gw.test.TestClass
class MyTestClass extends TestClass {
  function testSomething() {
    assert(true)
  }
}
```

#### 12. **Type Loaders**
- Gosu supports custom and built-in Type Loaders
- Used to load metadata and external types dynamically

---

### ⚙️ Gosu in Guidewire

- Used in PolicyCenter, BillingCenter, ClaimCenter
- Gosu code executes business rules, workflows, validation
- Guidewire Studio provides syntax highlighting and debugging support for Gosu

---

### 📄 Gosu API Usage

- Gosu can interact with Java classes directly
- Can consume REST APIs using Java libraries
- Easily integrates with Guidewire's internal APIs

---

### ❓ Common Interview Questions (Guidewire + Gosu)

1. **What is Gosu and how is it different from Java?**
   - Gosu is a statically typed language built on JVM, like Java. However, it includes features like type inference, enhancements, and named arguments that make it more expressive and suitable for business rules.

2. **Explain enhancements in Gosu with an example.**
   - Enhancements allow you to add methods to existing types. Example:
     ```gosu
     enhancement StringEnhancement : String {
       function shout() : String {
         return this.toUpperCase() + "!"
       }
     }
     ```

3. **How do named parameters work in Gosu?**
   - Named parameters allow calling methods with `:paramName = value` syntax, improving readability.
     ```gosu
     someMethod(:flag = true, :count = 5)
     ```

4. **What are delegates and how do you use them?**
   - Delegates let a class implement an interface via another object. You use `delegate` and `represents`.

5. **How does Gosu integrate with Guidewire products?**
   - Gosu is the scripting language used across Guidewire platforms to define business logic, validation rules, workflows, etc.

6. **How do you call Java code from Gosu?**
   - Directly use Java classes:
     ```gosu
     var now = java.util.Date()
     ```

7. **How does Gosu support business rule flexibility?**
   - Through enhancements, typelists, validation rules, expressions, and configuration layers.

8. **What are typelists and how are they used in Guidewire?**
   - Typelists define constrained sets of values (like enums) and support localization and validation.

9. **Explain the purpose of bundles in Guidewire.**
   - Bundles group DB operations to ensure consistency, support transactions, and enable rollback/commit.

10. **What are Gosu templates and how do they work?**
   - `.gsp` files allow mixing HTML and Gosu code to produce documents like emails or policy letters dynamically.

---

### 🎓 Summary

Gosu is a powerful language that complements Java by offering readable syntax, DSL features, and tight integration with Guidewire's insurance platforms. It promotes clean code, simplifies business rule development, and makes configuration more accessible to non-developers.

---

**Prepared By:** Abhishek  
