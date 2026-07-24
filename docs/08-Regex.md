# Regular Expressions (Regex)

## Objective

The objective of this section is to understand **Regular Expressions (Regex)** and their importance in Wazuh log analysis.

Regex is used in Wazuh for extracting important fields from raw logs during the decoder creation process. It helps identify patterns and extract information such as usernames, IP addresses, ports, commands, and other security-relevant data.

---

# What is Regex?

A **Regular Expression (Regex)** is a sequence of characters used to define a search pattern.

Regex helps security analysts identify and extract specific information from large amounts of log data.

Example:

Raw Log:

```
User Ishita logged in from 192.168.56.10
```

Regex:

```regex
User\s(\w+)\slogged\sin\sfrom\s(\S+)
```

Extracted Data:

```
Username: Ishita
IP Address: 192.168.56.10
```

---

# Importance of Regex in Wazuh

Wazuh receives logs in raw format. To understand these logs, Wazuh uses:

```
Raw Log
   ↓
Decoder
   ↓
Regex Pattern
   ↓
Extracted Fields
   ↓
Detection Rule
   ↓
Alert
```

Regex helps decoders identify specific information from logs and convert unstructured data into structured fields.

---

# Basic Regex Patterns

## 1. Literal Characters

Literal characters match exact text.

Example:

Log:

```
Failed login attempt
```

Regex:

```regex
Failed
```

Matches:

```
Failed
```

---

# 2. Character Classes

Character classes define a group of characters to match.

| Pattern | Description |
|---------|-------------|
| `[abc]` | Matches a, b, or c |
| `[0-9]` | Matches any digit |
| `[A-Z]` | Matches uppercase letters |
| `[a-z]` | Matches lowercase letters |

Example:

Regex:

```regex
[0-9]
```

Matches:

```
12345
```

---

# 3. Common Shortcuts

| Pattern | Description |
|---------|-------------|
| `\d` | Any digit |
| `\w` | Word character (letters, numbers, underscore) |
| `\s` | Whitespace |
| `\S` | Non-whitespace character |
| `.` | Any character |

Examples:

Match an IP address:

```regex
\d+\.\d+\.\d+\.\d+
```

Match a username:

```regex
\w+
```

---

# 4. Quantifiers

Quantifiers define how many times a character or group should appear.

| Pattern | Description |
|---------|-------------|
| `*` | Zero or more times |
| `+` | One or more times |
| `?` | Zero or one time |
| `{n}` | Exactly n times |
| `{n,m}` | Between n and m times |

Example:

Regex:

```regex
\d+
```

Matches:

```
12345
```

---

# 5. Capturing Groups

Parentheses are used to capture specific values from logs.

Example:

Log:

```
Username: Ishita
```

Regex:

```regex
Username:\s(\w+)
```

Extracted Field:

```
Ishita
```

The captured value can be used by Wazuh decoders.

---

# Regex Examples for Security Logs

## Example 1: Extract Username

Log:

```
User: admin
```

Regex:

```regex
User:\s(\w+)
```

Extracted:

```
admin
```

---

## Example 2: Extract IP Address

Log:

```
Connection received from 192.168.1.10
```

Regex:

```regex
(\d{1,3}\.){3}\d{1,3}
```

Extracted:

```
192.168.1.10
```

---

## Example 3: Extract Port Number

Log:

```
Connection established on port 443
```

Regex:

```regex
port\s(\d+)
```

Extracted:

```
443
```

---

# Regex Testing

Before using regex in Wazuh decoders, patterns should be tested to ensure correct matching.

Common testing platform:

```
regex101.com
```

Testing helps verify:

- Pattern accuracy
- Captured groups
- Extracted values
- Possible errors

---

# Regex in Wazuh Decoders

Wazuh decoders use regex to extract fields from logs.

Example decoder workflow:

```
Raw Event
    ↓
Pre-decoding
    ↓
Regex Matching
    ↓
Field Extraction
    ↓
Rule Detection
```

Example extracted fields:

```
srcip
user
command
process
status
```

---

# Key Learnings

- Learned the fundamentals of Regular Expressions.
- Understood how Regex helps in log parsing.
- Learned character classes, shortcuts, quantifiers, and capturing groups.
- Practiced extracting usernames, IP addresses, and ports from logs.
- Understood the role of Regex in Wazuh decoder development.

---

# Result

Regex concepts were successfully learned and applied to understand how Wazuh extracts meaningful information from raw security logs.

These concepts will be used in the next step for creating and testing custom Wazuh decoders.
