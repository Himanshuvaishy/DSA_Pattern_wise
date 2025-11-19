
# Valid Palindrome (Two Pointer Approach)

This solution checks if a string is a valid palindrome **without using regex**, using a clean and simple two-pointer technique.

---

## ✅ JavaScript Code (Simple & Clean)

```javascript
var isPalindrome = function(s) {
    let i = 0;
    let j = s.length - 1;

    const isAlphaNum = (ch) => {
        ch = ch.toLowerCase();
        return (
            (ch >= 'a' && ch <= 'z') || 
            (ch >= '0' && ch <= '9')
        );
    };

    while (i < j) {

        // skip non-alphanumeric from left
        while (i < j && !isAlphaNum(s[i])) i++;

        // skip non-alphanumeric from right
        while (i < j && !isAlphaNum(s[j])) j--;

        // compare both sides (lowercase)
        if (s[i].toLowerCase() !== s[j].toLowerCase()) {
            return false;
        }

        i++;
        j--;
    }

    return true;
};
```

---

## ✅ How it Works
- Two pointers: `i` (left) and `j` (right)
- Skip non-alphanumeric characters
- Compare lowercase characters
- If mismatch → false
- If loop ends → palindrome

---

## 🧪 Example

```javascript
isPalindrome("A man, a plan, a canal: Panama") // true
isPalindrome("race a car") // false



//! explantion 

✅ The line we are explaining:
return (
    (ch >= 'a' && ch <= 'z') || 
    (ch >= '0' && ch <= '9')
);


This line checks whether a character ch is alphanumeric (letter or digit).

🧠 Step-by-step Explanation
1️⃣ Characters have ASCII values

In JavaScript:

Characters like 'a', 'b', '1', '5'
are compared based on their ASCII values.

Example ASCII values:

'a' → 97

'z' → 122

'0' → 48

'9' → 57

So comparisons like:

ch >= 'a'


actually mean:

ASCII(ch) >= ASCII('a')

2️⃣ First part: (ch >= 'a' && ch <= 'z')

This checks:

👉 Is ch between 'a' and 'z'?

Meaning:

Is it 'a'?

'b'?

...

'z'?

So this entire condition is true only if ch is a lowercase letter.

Example:

ch	ASCII	Result
'b'	98	✔ between 97 and 122 → true
'z'	122	✔ → true
'A'	65	❌ not in range → false
3️⃣ Second part: (ch >= '0' && ch <= '9')

This checks:

👉 Is ch between '0' and '9'?

This means:

'0'

'1'

'2'

...

'9'

So this condition is true only if the character is a digit.

Example:

ch	ASCII	Result
'4'	52	✔ → true
'9'	57	✔ → true
'a'	97	❌ → false
4️⃣ Combining them using OR ||
(cond1) || (cond2)


Meaning:

✔ If character is a letter → return true
✔ If character is a digit → return true
❌ Otherwise return false

✅ Final Meaning (In English)

"Return true if the character is:
→ a lowercase letter (a–z)
OR
→ a digit (0–9)
Otherwise return false."

🧪 Example Walkthrough
Example 1: ch = 'c'
is 'c' >= 'a'? yes
is 'c' <= 'z'? yes
→ first condition true
→ return true

Example 2: ch = '7'
is '7' >= '0'? yes
is '7' <= '9'? yes
→ second condition true
→ return true

Example 3: ch = '%'
not a letter
not a number
→ return false

👍 Summary

The line:

return (
    (ch >= 'a' && ch <= 'z') || 
    (ch >= '0' && ch <= '9')
);


is basically doing:

"Is ch a letter or a number?"
```
