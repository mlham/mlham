# Beginner's Guide to GitHub Flavored Markdown (GFM)

GitHub Flavored Markdown (GFM) is an **enhanced version of Markdown** used on GitHub for documentation, issues, pull requests, and wikis. It extends standard Markdown by adding features like **tables, task lists, and strikethrough text**.

---

## **1. Formatting Text in Markdown**

### **Headings**

Headings structure your document. Use `#` symbols:

```markdown
# H1 (Largest)
## H2
### H3
#### H4
##### H5
###### H6 (Smallest)
```

### **Bold, Italic, and Strikethrough**

- **Bold** → `**bold text**`
- *Italic* → `*italic text*`
- ***Bold and Italic*** → `***both styles***`
- ~~Strikethrough~~ → `~~crossed-out text~~`

Example:

```markdown
This is **bold**, *italic*, ***italic and bold*** and ~~crossed out~~.
```

This is **bold**, *italic*, ***italic and bold***, and ~~crossed out~~.

---

## **2. Lists and Task Lists**

### **Unordered Lists**

Use `-`, `*`, or `+` for bullet points.

```markdown
- Item 1
- Item 2
  - Subitem 1
  - Subitem 2
```

- Item 1
- Item 2
  - Subitem 1
  - Subitem 2
  
### **Ordered Lists**

Use numbers followed by a period.

```markdown
1. First item
2. Second item
   1. Sub-item
   2. Sub-item
```

1. First item
2. Second item
   1. Sub-item
   2. Sub-item

### **Task Lists**

Task lists allow **checkboxes** in GitHub issues and pull requests.

```markdown
- [ ] Task not done
- [x] Task completed
```

- [ ] Task not done
- [x] Task completed

> **Tip:** In GitHub issues and PRs, you can **click the checkboxes** to toggle them and add a completion
> amount based on how many/much of the boxes are checked. 

---

## **3. Tables**

Tables use `|` (pipes) and `-` (dashes).

### **Basic Table**

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Data     | More Data |
| Row 2    | Example  | Text      |
```

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Data     | More Data |
| Row 2    | Example  | Text      |

### **Aligned Columns**

Align text using colons (`:`).

```markdown
| Left      | Centered | Right      |
|:--------- |:--------:|----------:|
| Text      | Text     | Text      |
| More Text | More Text | More Text |
```

| Left      | Centered | Right      |
|:--------- |:--------:|----------:|
| Text      | Text     | Text      |
| More Text | More Text | More Text |

> **Tip:** Use colons to align **left**, **center**, or **right**.

---

## **4. Code Blocks**

Use backticks (`) for inline code:  
Example: `` `console.log("Hello")` `` → `console.log("Hello")`

For larger blocks, use triple backticks:

```javascript
function greet() {
   console.log("Hello, world!");
}
```

> **Tip:** Add a language (`javascript`, `python`, etc.) for syntax highlighting.

---

## **5. Front Matter (For Static Site Generators)**

Front matter is metadata at the **top of a Markdown file**, enclosed in `---`. Used in **Jekyll, Hugo, Eleventy**, etc.

### **Example**

```markdown
---
title: "My Blog Post"
author: "Jane Doe"
date: "2025-03-13"
tags: ["markdown", "GFM", "guide"]
draft: false
---
```

> **Note:** **Front matter must be the first content in the file.** No empty lines above it!

---

## **6. markdownlint: Enforcing Markdown Standards**

markdownlint helps maintain **consistent** Markdown formatting. It prevents **common mistakes** and enforces **style consistency** in documentation.

### **Common markdownlint Rules**

```markdown
| Rule      | Description                                  | Why It's Useful                        |
|-----------|----------------------------------------------|----------------------------------------|
| **MD013** | Line length limit                           | Prevents unreadable long lines        |
| **MD033** | HTML in Markdown                            | Avoids raw HTML in docs               |
| **MD041** | First line should be a heading             | Ensures clarity in docs               |
| **MD022** | Headers should be surrounded by blank lines | Improves readability                  |
| **MD032** | Lists should be surrounded by blank lines   | Improves structure                    |
```

---

## **7. Excluding markdownlint Rules for HTML**

If you need raw HTML in Markdown but **don’t want markdownlint to flag it**, use:

```markdown
<!-- markdownlint-disable MD013 MD033 MD041 -->
<div style="color: red; font-weight: bold;">
   This is an HTML block inside Markdown.
</div>
<!-- markdownlint-enable MD013 MD033 MD041 -->
```

### **Why Disable These Rules?**

- **MD013 (Line Length)** → Allows longer inline HTML without warnings.  
- **MD033 (Raw HTML)** → Prevents markdownlint from flagging `<div>` and other tags.
- **MD041 (First Line Heading)** → Avoids conflicts when using **front matter** at the top.

---

## **8. Key Takeaways**

- **Markdown is simple**, but GFM adds extra features like **task lists, tables, and syntax highlighting**.
- **Use markdownlint** to enforce **consistent documentation standards**.
- **HTML inside Markdown** can be allowed with proper **markdownlint exclusions**.
- **Front matter** is essential for static site generators like **Jekyll, Hugo, and Eleventy**.

