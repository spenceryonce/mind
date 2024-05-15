---
tags:
  - programming
  - javascript
  - regex
  - challenge
  - code
---

# Name Validation
A term is either an initials or word.
initials = 1 character
words = 2+ characters (no dots allowed)
A valid name is a name written in one of the following ways:

Rules
Both initials and words must be capitalized.
Initials must end with a dot.
A name must be either 2 or 3 terms long.
If the name is 3 words long, you can expand the first and middle name or expand the first name only. You cannot keep the first name as an initial and expand the middle name only.
The last name must be a word (not an initial).

H. Wells
H. G. Wells
Herbert G. Wells
Herbert George Wells

Herbert
Wells 
H Wells
H. G Wells
h. Wells
H. wells
h. g. Wells 
H. George Wells 
H. G. W.
Herb. G. Wells 

match
match
match
match

none
none
none
none
none
none
none
none
none
none

## The Solution

#### Level 1
This was my solution. Solved at 11:52pm Friday, May 3, 2024. After about 2 hours of trying to get the regex to do its thing.
```js
function isValidName(name) {
    const check1 = /^(([A-Z]\.\s){1,2}[A-Z][a-z]+|[A-Z][a-z]+(\s[A-Z]\.)?\s[A-Z][a-z]+)$/;
    const check2 = /^[A-Z][a-z]+\s[A-Z][a-z]+\s[A-Z][a-z]+$/;
    
    return check1.test(name) || check2.test(name);
}

// Testing the function
console.log(isValidName('H. G. Wells')); // true
console.log(isValidName('H. Wells')); // true
console.log(isValidName('Herbert G. Wells')); // true
console.log(isValidName('Herbert George Wells')); // true
console.log(isValidName('Herbert')); // false
console.log(isValidName('H Wells')); // false
console.log(isValidName('H. G Wells')); // false
console.log(isValidName('Herbert G. W.')); // false
```
#### Level 2
```js
function validName(name) {
	return /^([A-Z]\.( [A-Z]\.)?|[A-Z]\w+ [A-Z]\w+|[A-Z]\w+ [A-Z]\.)( [A-Z]\w+)$/.test(name)
}
```





