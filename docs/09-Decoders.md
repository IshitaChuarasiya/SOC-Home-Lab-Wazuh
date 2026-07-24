# Wazuh Decoders

## Objective

The objective of this task was to understand the role of **Wazuh Decoders** and how they are used to extract meaningful information from raw log data.

Decoders help Wazuh analyze incoming logs by identifying their structure, extracting important fields, and preparing the data for security rule matching and alert generation.

---

# What are Wazuh Decoders?

Wazuh Decoders are responsible for parsing and analyzing raw log messages received by the Wazuh Manager.

They convert unstructured log data into structured information that can be understood by Wazuh detection rules.

Example workflow:

```
Raw Log
   ↓
Decoder
   ↓
Regex Extraction
   ↓
Structured Fields
   ↓
Detection Rule
   ↓
Alert
```

---

# Importance of Decoders

Security devices and endpoints generate logs in different formats.

Example raw log:

```
Username: Ishita
```

A decoder extracts useful information from this log:

```
Field:
username

Value:
Ishita
```

The extracted information can then be used for:

- Log analysis
- Detection rules
- Alert generation
- Security investigations

---

# Decoder Components

A Wazuh decoder consists of different components:

| Component | Description |
|-----------|-------------|
| Decoder Name | Identifies the decoder |
| Parent Decoder | Allows inheritance from another decoder |
| Prematch | Identifies matching log patterns |
| Regex | Extracts required information |
| Order | Defines extracted field names |

---

# Types of Decoders

## Parent Decoder

A parent decoder identifies the general structure or type of a log.

Example:

```xml
<decoder name="custom-userlog">
</decoder>
```

---

## Child Decoder

A child decoder inherits from a parent decoder and performs additional extraction.

Workflow:

```
Parent Decoder
        ↓
Child Decoder
        ↓
Field Extraction
```

---

# Creating a Custom Decoder

A custom decoder was created to extract username information from the following log:

```
Username: Ishita
```

The objective was to extract the username value using a regular expression.

---

# Decoder Configuration

Custom decoder location:

```
/var/ossec/etc/decoders/local_decoder.xml
```

Configuration:

```xml
<decoder name="custom-userlog">
    <prematch>Username:</prematch>
</decoder>

<decoder name="custom-userlog">
    <regex>Username:\s(\w+)</regex>
    <order>username</order>
</decoder>
```

---

# Understanding the Regex

Regex used:

```regex
Username:\s(\w+)
```

Explanation:

| Pattern | Meaning |
|---------|---------|
| Username: | Matches exact text |
| \s | Matches whitespace |
| (\w+) | Captures username value |

Example:

Input:

```
Username: Ishita
```

Extracted value:

```
username = Ishita
```

---

# Testing Decoder Using Wazuh Logtest

After creating the decoder, it was tested using the Wazuh log testing utility.

Command:

```bash
/var/ossec/bin/wazuh-logtest
```

Test input:

```
Username: Ishita
```

---

# Decoder Testing Phases

## Phase 1: Pre-decoding

The first phase identifies the basic structure of the incoming log.

Example output:

```
Phase 1: Completed pre-decoding
```

---

## Phase 2: Decoding

The second phase applies the decoder and extracts information from the log.

Example output:

```
Phase 2: Completed decoding
name: custom-userlog
```

---

# Decoder Workflow in Wazuh

The complete decoder workflow:

```
Incoming Log
      ↓
Pre-decoding
      ↓
Decoder Matching
      ↓
Regex Extraction
      ↓
Field Creation
      ↓
Rule Evaluation
      ↓
Alert Generation
```

---

# Common Uses of Decoders

Wazuh decoders can be used to extract:

- Usernames
- IP addresses
- Ports
- Process names
- Commands
- File paths
- Authentication information

---

# Key Learnings

- Learned the purpose of Wazuh Decoders.
- Understood how raw logs are converted into structured data.
- Learned the difference between parent and child decoders.
- Created a custom decoder using Regex.
- Learned how extracted fields can be used for detection.
- Understood the role of decoders in SIEM log processing.

---

# Result

A custom Wazuh decoder was created to parse raw log data and extract meaningful fields.

This improved understanding of how Wazuh processes logs before applying detection rules and generating security alerts.
