# Dart Programming Basics

![Dart Logo](https://upload.wikimedia.org/wikipedia/commons/7/7e/Dart-logo.png)

This document tests all markdown elements with the improved Flutter markdown styles.

## Table of Contents

1. [Headings](#headings)
2. [Text Formatting](#text-formatting)
3. [Lists](#lists)
4. [Links](#links)
5. [Code](#code)
6. [Blockquotes](#blockquotes)
7. [Tables](#tables)
8. [Horizontal Rules](#horizontal-rules)
9. [Task Lists](#task-lists)

---

## Headings

# H1 - Main Title (Pale Purple)
## H2 - Section Title (Pale Blue)
### H3 - Subsection Title (Pale Teal)
#### H4 - Minor Heading (Pale Green)
##### H5 - Small Heading (Pale Yellow)
###### H6 - Tiny Heading (Pale Pink)

---

## Text Formatting

This is **bold text** and this is *italic text*.

You can also use __bold__ and _italic_ formatting.

~~Strikethrough text~~ is also supported.

Here's some `inline code` within a paragraph.

---

## Lists

### Unordered List
- First item
- Second item
  - Nested item
  - Another nested item
- Third item

### Ordered List
1. First numbered item
2. Second numbered item
   1. Nested numbered item
   2. Another nested item
3. Third numbered item

---

## Links

Here's a [link to Google](https://google.com).

You can also use reference-style links like [this one][ref].

[ref]: https://github.com

---

## Code

### Inline Code
Use the `print()` function to display output.

### Code Blocks

```dart
// Flutter Dart code example
class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(16.0),
      child: Text(
        'Hello, World!',
        style: TextStyle(
          fontSize: 24,
          fontWeight: FontWeight.bold,
          color: Colors.blue,
        ),
      ),
    );
  }
}
```

```javascript
// JavaScript code example
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

const result = fibonacci(10);
console.log(`Fibonacci of 10 is: ${result}`);
```

```python
# Python code example
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quicksort(left) + middle + quicksort(right)

# Example usage
numbers = [3, 6, 8, 10, 1, 2, 1]
sorted_numbers = quicksort(numbers)
print(sorted_numbers)
```

```json
{
  "name": "markdown-test",
  "version": "1.0.0",
  "description": "Testing markdown rendering",
  "keywords": ["markdown", "flutter", "testing"],
  "author": "Developer",
  "dependencies": {
    "flutter": "^3.0.0",
    "flutter_markdown": "^0.6.0"
  }
}
```

---

## Blockquotes

> This is a blockquote. It can contain multiple paragraphs and other markdown elements.
> 
> Here's a second paragraph in the blockquote.
> 
> - Even lists work
> - Inside blockquotes

> ### Nested Elements
> 
> You can nest other markdown elements inside blockquotes:
> 
> ```dart
> // Code blocks work too
> void main() {
>   print('Hello from blockquote!');
> }
> ```

---

## Tables

| Feature | Dark Theme | Light Theme | Status |
|---------|------------|-------------|---------|
| Headings | ✅ Pale Colors | ✅ Soft Colors | Complete |
| Code Blocks | ✅ GitHub Style | ✅ GitHub Light | Complete |
| Lists | ✅ Pale Bullets | ✅ Soft Bullets | Complete |
| Links | ✅ Pale Blue | ✅ Soft Blue | Complete |
| Tables | ✅ Subtle | ✅ Clean | Complete |

### Table with Alignment

| Left Aligned | Center Aligned | Right Aligned |
|:-------------|:--------------:|--------------:|
| Left | Center | Right |
| Text | Text | Text |
| More | Content | Here |

---

## Horizontal Rules

Above this line, you'll see a horizontal rule.

---

Below this line, there's another horizontal rule.

---

## Task Lists

- [x] Implement heading styles
- [x] Add code block styling
- [x] Create blockquote design
- [x] Design table formatting
- [ ] Add syntax highlighting
- [ ] Test on different devices
- [ ] Performance optimization

### Nested Task Lists

- [x] Main task completed
  - [x] Subtask 1 done
  - [x] Subtask 2 done
  - [ ] Subtask 3 pending
- [ ] Second main task
  - [ ] Subtask A
  - [ ] Subtask B

---

## Mixed Content Example

Here's a complex example combining multiple elements:

### API Documentation Example

The `getUserData()` function returns user information:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  isActive: boolean;
}

async function getUserData(userId: number): Promise<User> {
  try {
    const response = await fetch(`/api/users/${userId}`);
    if (!response.ok) {
      throw new Error('Failed to fetch user data');
    }
    return await response.json();
  } catch (error) {
    console.error('Error fetching user:', error);
    throw error;
  }
}
```

> **Note:** This function requires authentication. Make sure to include the authorization header in your request.

#### Response Format

| Field | Type | Description |
|-------|------|-------------|
| `id` | number | Unique user identifier |
| `name` | string | User's full name |
| `email` | string | User's email address |
| `isActive` | boolean | Whether the user is active |

#### Usage Example

1. Import the function
2. Call with user ID
3. Handle the response

```javascript
// Example usage
getUserData(123)
  .then(user => {
    console.log('User data:', user);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

---

## Conclusion

This test file demonstrates all major markdown elements with the improved styling:

- **Headings** use pale/soft colors for better visual hierarchy
- **Code blocks** follow GitHub's color scheme for familiarity
- **Other elements** use subtle, pale colors for a cohesive look
- **Spacing** is optimized for readability
- **Typography** is consistent throughout

The styling works well in both dark and light themes, providing a professional and readable markdown experience.
