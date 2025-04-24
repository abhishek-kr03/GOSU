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
1. What is Gosu and how is it different from Java?
2. Explain enhancements in Gosu with an example.
3. How do named parameters work in Gosu?
4. What are delegates and how do you use them?
5. How does Gosu integrate with Guidewire products?
6. How do you call Java code from Gosu?
7. How does Gosu support business rule flexibility?

---

### 🎓 Summary
Gosu is a powerful language that complements Java by offering readable syntax, DSL features, and tight integration with Guidewire's insurance platforms. It promotes clean code, simplifies business rule development, and makes configuration more accessible to non-developers.

---

**Prepared By:** Abhishek
