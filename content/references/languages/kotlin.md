---
date: '2025-05-22T17:16:30-07:00'
draft: false
title: 'Kotlin Language Reference'
summary: ' '
---

{{< gist mwtaylor 7f89e3d8334c983bbfd2153e0d1014d9 >}}

{{< toc >}}

# I/O

## Output

### stdout

`print(...)` to print something without a newline, and `println(...)` to
print with a newline at the end. `println()` with no args to start a new
line.

### stderr

Nothing built in to Kotlin to print to stderr. Use Java functions when
running on the JVM.

```kotlin
System.err.println("Error!")
```

### Logging

Use available Java logging libraries. Generally will look like this:

```kotlin
class MyClass {
    companion object {
        val LOG = Logger.getLogger(MyClass::class.java.name) 
    }

    fun foo() {
        LOG.warning("Uh-oh")
    }
} 
```

In Android:

```kotlin
Log.w("Something bad")
```

## Command Line Arguments

```kotlin
fun main(args: Array<String>) {
    println(args.size)
    println(args.contentToString())
}
```

Output from input "x y z":
```text
3
[x, y, z]
```

## Text Input

```kotlin
val input = readln()
val i = readln().toIntOrNull()
```

Use `readlnOrNull()` to return null if end of input is reached, otherwise 
`readln()` throws an exception.

### Scanner

Usually it is best to use a Java Scanner. 

```kotlin
import java.util.Scanner

val scanner = Scanner(System.`in`)

val line = scanner.nextLine()
val i = scanner.nextInt()

scanner.close()
```

Call close when done or take advantage of `AutoCloseable` resource.

```kotlin
Scanner(System.`in`).use { scanner ->
    //...
}
```

# References

- https://kotlinlang.org/docs/getting-started.html
- https://kotlinlang.org/docs/coding-conventions.html
- https://play.kotlinlang.org
