# MatchTheRegex

## Platform
picoCTF

## Category
Web Exploitation

## Difficulty
Medium

---

## 🧠 Challenge Overview

The "MatchTheRegex" challenge demonstrates a classic **Regex Injection vulnerability** caused by improper handling of user input in a web application.

The application accepted user input and used it directly inside a regular expression on the backend instead of performing a strict string comparison. Because of this, user input was interpreted as a regex pattern rather than plain text.

---

## 🔍 Initial Analysis

While interacting with the application:

- The input field appeared to validate whether a submitted value matched a hidden string.
- The validation logic did not rely on strict equality comparison.
- The behavior suggested pattern-based matching rather than literal comparison.

Based on the challenge name and observed behavior, it was likely that the backend was evaluating user input as a regular expression.

---

## 🛠 Exploitation Concept

The backend logic was likely implemented in a way similar to:

```javascript
flag.match(userInput)
// or
new RegExp(userInput)
```

Instead of comparing strings directly, the application constructed a regular expression using user-supplied input.

Because regular expressions treat certain characters as operators (such as `*`, `.`, `+`, etc.), this allowed manipulation of the matching logic.

The vulnerability occurred because user input was treated as executable pattern logic rather than plain data.

---

## 📘 Regex Notes

A **Regular Expression (Regex)** is a pattern used to match character combinations in strings. It is widely used in:

- Input validation
- Searching
- Filtering
- Parsing structured text

---
