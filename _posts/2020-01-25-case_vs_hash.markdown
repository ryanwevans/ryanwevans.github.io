---
layout: post
title:      "Case vs. Hash"
date:       2020-01-25 22:21:54 -0500
permalink:  case_vs_hash
---


I was working on a text editor code challenge in Ruby recently.  The solution had to accept input that included an operation number.  Each operation number represented a method that would execute the corresponding operation.  For example, operation 1 should call the `append()` method, which adds characters to a string.  Operation 2 should call the `delete()` method that removes characters from the string, and so on.
<br/>
<br/>
A common way to solve this, is to create a case statement.  It can also be done with an if/else statement, but the problem with an if/else statement is that if you were to add more operations, it'll get cumbersome quickly.
<br/>
<br/>
Let's take a look at what the case statement might look like:
```
case @operation_number {
  when 1
	 append(characters)
  when 2
	 delete(characters)
  else
	 raise 'Please enter a valid operation number'
  end
}
```

<br/>
But there's another approach.  You can use the built in Ruby `send()` method in conjunction with a hash, setting the operation number as the key, and the method (`append()`, `delete()`, etc.) as the corresponding value.
<br/>
<br/>
This approach makes adding and updating methods quick and easy.  And more importantly, hashes have much faster lookups.  So imagine having to find the correct operation out of hundreds of operations/methods.  In that scenario, a case statement would be noticeably slower to find the correct operation than a hash.
<br/>
<br/>
Here's what the hash code looks like:
```
OPERATIONS = {1 => :append, 2 => :delete}

def run_operation(num, arg)
    if OPERATIONS.key?(num)
        send(OPERATIONS[num], *arg)
    else
        raise 'Please enter a valid operation'
    end
end
```

<br/>
The `send()` method checks for `OPERATIONS[num]`, and if there is a match, it calls the corresponding method and passes any included arguments (`*arg`).
<br/>
<br/>
Here's a link to the [Ruby documentation](https://ruby-doc.org/core-2.6.3/Object.html#method-i-send) on `send()`.
<br/>
<br/>
Happy coding!





