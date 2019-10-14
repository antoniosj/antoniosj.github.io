---
title:  "Understanding Swift closures"
date:   2019-05-21 22:00:00
categories: [swift]
tags: [Swift, Mobile, iOS]
---

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">At <a href="https://www.cesar.org.br/">@cesar</a> we have some open source projects and we use the Sticky Sessions app for our retrospective meetings. At first we developed the Android version because we have more Android users, but then, we started to develop the iOS version which was completely new for some people here.</p> 

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">One thing that causes some struggling to understand is swift closures. And when I studied swift by the course of Angela Yu, I saw a nice explanation to what is swift closures.</p> 

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Well, swift closures is defined by Apple as self contained blocks of functionality that are passed around. Imagine a function where you can pass an input and return an output. With closures, you can pass a function and return a function too, as the examples bellow:</p>

```swift
func calculator(n1: Int, n2: Int) -> Int { 
  return n1 * n2
}

calculator(n1: 3, n2: 4)
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Now you can add a function as argument and do this:</p>

```swift
func calculator(n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int { 
  return operation(n1, n2)
}
  
func add(n1: Int, n2: Int) -> Int {
  return n1 + n2
}
  
calculator(n1: 3, n2: 4, operation:add)
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">If you want to cut this a bit, you can use closures. First, remove the keyword func and the name of the function, then move the first brackt to the begining and after that, add the keyword right after the return type:</p>

```swift
{ (n1: Int, n2: Int, add: (Int, Int) -> Int) -> Int in  
      return n1 + n2
}
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">And now we have this:</p>

```swift
func calculator(n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int { 
  return operation(n1, n2)
}
  
calculator(n1: 3, n2: 4, operation: { (n1: Int, n2: Int) -> Int) -> Int in  
      return n1 + n2
})
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">We can make things even better. Swift has the ability to infer data types based on the value, called Typed inference. And you can delete the return keyword as swift infers that the operation has a return too.</p>

```swift
func calculator(n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int { 
  return operation(n1, n2)
}
  
calculator(n1: 3, n2: 4, operation: { (n1, n2) in 
n1 + n2 
})
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">If you want to go extreme though, as n1 and n2 are returned as a operation using the same arguments, you can use $0 and $1 (indicating first and second argument respectively) and as your closure is the last parameter, you can omit the its name and the keyword in.</p>

```swift
func calculator(n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int { 
  return operation(n1, n2)
}
  
calculator(n1: 3, n2: 4) { $0 + $1 }
```

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Buy you don't need to do this extreme always. In general, closure expression syntax has the following form:</p>

```swift
{ (parameter) -> return type in
    statments
}
```

// under construction //
