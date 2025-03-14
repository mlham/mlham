---
title: "Markdown with Gherkin (MDG) Guide"
---
<!-- markdownlint-disable MD025 -->
# Markdown with Gherkin (MDG)
<!-- markdownlint-enable MD025 -->

**Markdown with Gherkin (MDG)** is a **strict superset of GitHub Flavored Markdown (GFM)** that allows embedding **Gherkin scenarios** inside Markdown. MDG files use the `.feature.md` extension to
differentiate them from regular Markdown files.

## **1. Basic Structure of MDG**

An MDG file consists of:

1. **Feature Definition**
2. **Rules (Optional)**
3. **Scenarios & Scenario Outlines**
4. **Steps (`Given`, `When`, `Then`, `And`, `But`)**
5. **Data Tables & Examples Tables**
6. **Doc Strings**
7. **Tags**

Each of these sections **follows Gherkin syntax** but is adapted to Markdown.

---

## **2. Sections in MDG**

### **2.1 Feature Definition**

- A **feature** describes the functionality being tested.
- It must be declared using a **Markdown heading (`# Feature`)**.
- If omitted, the **first line of the document** becomes the feature title.

#### **Example: Features**

```markdown
# Feature: User Login

A user should be able to log in with valid credentials.
```

---

### **2.2 Rules (Optional)**

- **Rules** help organize related scenarios within a feature.
- They must be declared using `## Rule`.

#### **Example: Rules**

```markdown
## Rule: Account must be active

Users with inactive accounts cannot log in.
```

---

### **2.3 Scenarios & Scenario Outlines**

- **Scenarios** describe test cases and begin with `### Scenario`.
- **Scenario Outlines** use placeholders (`<value>`) and are followed by `#### Examples`.

#### **Example: Scenarios**

```markdown
### Scenario: User logs in successfully

* Given a registered user exists
* When they enter valid credentials
* Then they should see their dashboard
```

#### **Scenario Outline Example:**

```markdown
### Scenario Outline: Logging in with multiple users

* Given a user with username `<username>` and password `<password>`
* When they attempt to log in
* Then they should see `<message>`

#### Examples: Scenario Outline

  | username   | password | message         |
  |-----------|----------|----------------|
  | alice     | pass123  | "Welcome Alice!" |
  | bob       | secret   | "Welcome Bob!" |
```

---

### **2.4 Steps (`Given`, `When`, `Then`, `And`, `But`)**

- Steps must be **Markdown list items (`-` or `*`)**.
- Keywords:
  - `Given` → **Initial context**
  - `When` → **Action performed**
  - `Then` → **Expected outcome**
  - `And` / `But` → **Additional conditions**

#### **Example: Steps**

```markdown
### Scenario: Adding a product to the cart

* Given the user is on the product page
* When they click "Add to Cart"
* Then the product should be added to their cart
* And the cart should display 1 item
```

---

### **2.5 Data Tables & Examples Tables**

- **Tables must be indented 2-5 spaces** for MDG to recognize them.
- Tables use **GFM table syntax** (`|` for columns, `-` for headers).

#### **Example: Table**

```markdown
### Scenario: Shopping cart with multiple items

* Given the following items in the cart:

  | Product   | Quantity | Price  |
  |----------|----------|--------|
  | Laptop   | 1        | $1000  |
  | Mouse    | 2        | $20    |

* When the user proceeds to checkout
* Then the total price should be $1040
```

---

### **2.6 Doc Strings**

- **Doc Strings use GFM fenced code blocks** (```).
- They store **multi-line data** such as JSON, XML, or logs.

#### **Example: Doc Strings**

<!-- markdownlint-disable MD004 MD040 -->

````markdown
### Scenario: API responds with user details

* Given the API returns the following response:

  ```
  {
    "id": 123,
    "username": "john_doe",
    "role": "admin"
  }
  ```

* Then the user should see "Admin Dashboard"

````

<!-- markdownlint-enable MD004 MD040 -->

---

### **2.7 Tags**

- **Tags must be enclosed in backticks (`)**
- **Tags must be placed above scenarios**

#### **Example: Tags**

```markdown
`@smoke` `@login`
### Scenario: User logs in successfully

* Given a registered user exists
* When they enter valid credentials
* Then they should see their dashboard
```

---

## **3. Differences Between Classic Gherkin & MDG**

| Feature           | Classic Gherkin | Markdown with Gherkin (MDG) |
|------------------|---------------|-----------------------------|
| **File Extension** | `.feature` | `.feature.md` |
| **Feature Definition** | `Feature:` keyword | `# Feature` Markdown heading |
| **Scenario Definition** | `Scenario:` keyword | `### Scenario` Markdown heading |
| **Steps** | No bullet points | Uses `*` or `-` list items |
| **Examples Table** | `Examples:` keyword | `#### Examples:` heading |
| **Doc Strings** | Triple quotes (`"""`) | GFM fenced code blocks (```) |

---

## **4. Rendering MDG Files**

- MDG files **can be rendered** by any **GitHub Flavored Markdown (GFM) renderer**.
- They can also be parsed by **Gherkin-based tools like Cucumber**.

### **4.1 Rendering MDG with Cucumber**

- The [`@cucumber/react`](https://github.com/cucumber/cucumber-react) library provides an `<MDG>` React component.
- This component **renders MDG files** with Cucumber test results.

---

## **5. Notes About MDG Parsing**

- MDG uses the **same Gherkin parser** as classic Gherkin.
- The `GherkinInMarkdownTokenMatcher`:
  - Treats **non-Gherkin lines** as **empty** (ignored).
  - Keeps **empty description properties** in the JSON output.

> **Important:** Currently, **only the JavaScript implementation** of Gherkin (`@cucumber/gherkin` v19.0.0+) supports MDG.

---

## **6. Summary**

- **MDG is a superset of GFM, making it both readable and testable.**  
- **Uses Markdown headings for feature/scenario definitions.**  
- **Lists (`*` or `-`) replace traditional Gherkin step syntax.**  
- **Tables must be indented (2-5 spaces) for MDG to recognize them.**  
- **Supports tags, doc strings, and examples tables just like classic Gherkin.**  
