# 🔐 Document Password Security & Hash Cracking

### Cybersecurity Internship | Week 3 | NetworkWalks

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Focus](https://img.shields.io/badge/Focus-Password%20Security-blue)
![Tools](https://img.shields.io/badge/Tools-John%20the%20Ripper%20%7C%20NetworkWalks-orange)
![Status](https://img.shields.io/badge/Project-Practical%20Lab-success)

---

## 1. Project Overview

This project explores the security mechanisms behind password-protected documents, focusing on hash extraction, cryptographic hash analysis, and password recovery techniques.

The exercise was carried out as part of my Week 3 cybersecurity internship training at **NetworkWalks**.

The primary objective was to understand how password-protected documents can be assessed using specialised security tools, how document hashes are extracted, and how password-cracking techniques can be applied to evaluate password strength.

The practical exercise involved working with **John the Ripper**, **NetworkWalks Official Hash Calculator**, and **NetworkWalks Password Kcracker**.

Rather than treating password protection as an isolated security feature, this exercise examined the underlying processes that make password auditing and recovery possible.

## 2. Project Objectives

The major objectives of this exercise were to:

- Understand the relationship between document encryption, password protection, and cryptographic hashing.
- Extract password hashes from protected documents.
- Examine cryptographic hashes and understand their representation.
- Use John the Ripper to perform hash-based password auditing.
- Explore password recovery techniques, including dictionary-based attacks.
- Understand how weak and predictable passwords can compromise document security.
- Examine the importance of strong password policies and secure document handling.

## 3. Tools and Technologies

The following tools were explored during the exercise.

| Tool | Purpose |
|---|---|
| John the Ripper | Password auditing and hash-based password recovery. |
| NetworkWalks Official Hash Calculator | Generating and examining cryptographic hashes. |
| NetworkWalks Password Kcracker | Exploring password recovery techniques. |
| pdf2john | Extracting password hash information from protected PDF documents for use with John the Ripper. |
| Command Line / Terminal | Executing commands and interacting with the security tools. |

### 3.1 John the Ripper

John the Ripper is an open-source password security auditing and recovery tool.

It supports multiple password hash formats and employs different techniques to identify weak passwords.

Some of its capabilities include:

- Dictionary attacks.
- Brute-force password attempts.
- Incremental password attacks.
- Hash identification and password auditing.
- Password recovery from supported hash formats.

In this exercise, John the Ripper was used to work with extracted document hashes and explore the password recovery process.

### 3.2 NetworkWalks Official Hash Calculator

The NetworkWalks Official Hash Calculator was used to explore cryptographic hash generation and analysis.

Hash functions transform input data into fixed-length outputs, commonly referred to as hash digests.

The exercise provided an opportunity to examine how different inputs produce different hash representations and understand the role of hashing in cybersecurity.

### 3.3 NetworkWalks Password Kcracker

The NetworkWalks Password Kcracker was another tool explored during the practical exercise.

It provided an additional environment for examining password recovery techniques and understanding how password-cracking tools approach protected credentials.

Using multiple tools helped reinforce the relationship between password analysis, hash processing, and recovery techniques.

### 3.4 pdf2john

pdf2john is a utility distributed with John the Ripper Jumbo.

It extracts password-verification information from supported PDF documents and converts it into a format that John the Ripper can process.

This is particularly useful when assessing the password strength of encrypted PDF files.

---

## 4. Understanding the Technical Concepts

Before examining the practical workflow, it is important to distinguish between three related concepts.

**Document Encryption**

Encryption protects document contents by transforming readable information into an encrypted form that requires the appropriate credentials or cryptographic key for access.

**Cryptographic Hashing**

Hashing converts input data into a fixed-length digest using a mathematical function.

Hashes are commonly used in authentication, integrity verification, and password storage systems.

**Password Cracking**

Password cracking involves attempting to recover an original password by testing possible candidates against a password verifier or extracted hash.

An important distinction is that document encryption and password hashing are not the same thing. An extracted PDF hash is generally a representation of the information needed to test password guesses, not the document's encryption key itself.

---

## 5. Practical Methodology

The exercise followed a structured workflow.

### Phase 1: Preparation

A password-protected document was selected as the test file.

The objective was to examine how password protection could be assessed without modifying or compromising unrelated files.

The required tools were prepared, including John the Ripper and the relevant hash extraction utility.

### Phase 2: Hash Extraction

The next step involved extracting password-verification information from the protected document.

For PDF documents, the pdf2john utility can be used.

Example command:

```bash
python pdf2john.py protected_document.pdf > document_hash.txt
```

Depending on the installation, the utility may also be invoked using its Perl script:

```bash
perl pdf2john.pl protected_document.pdf > document_hash.txt
```

The resulting output is saved in a text file for subsequent analysis.

**Expected output:** A hash representation containing the information required by John the Ripper to attempt password recovery.

### Phase 3: Hash Analysis

The extracted hash was examined to understand its structure and determine whether it was suitable for processing by the password auditing tool.

This stage is important because password-cracking utilities require compatible hash formats.

Incorrect extraction, unsupported formats, or malformed hash files can prevent successful processing.

### Phase 4: Password Auditing with John the Ripper

John the Ripper was used to process the extracted hash.

A typical command is:

```bash
john document_hash.txt
```

To perform a dictionary-based attack using a specified wordlist:

```bash
john --wordlist=wordlist.txt document_hash.txt
```

To display previously recovered passwords:

```bash
john --show document_hash.txt
```

To inspect the current cracking session:

```bash
john --status
```

The effectiveness of password recovery depends on several factors, including:

- Password complexity and length.
- The cracking technique employed.
- The available wordlist.
- The hash format and computational cost.
- Available processing resources.

### Phase 5: Hash Calculation and Analysis

The NetworkWalks Official Hash Calculator was explored to examine the generation and representation of cryptographic hashes.

Different input values can be processed to observe how changes in the input affect the resulting digest.

This reinforces the importance of cryptographic hashing in security applications.

### Phase 6: Password Recovery Exploration

The NetworkWalks Password Kcracker was explored as an additional password recovery utility.

This provided another perspective on password auditing and the techniques used to evaluate password strength.

The exercise reinforced the importance of understanding how password recovery tools operate rather than relying solely on their output.

---

## 6. Key Observations and Technical Findings

Several important concepts emerged from the exercise:

**1. Password protection does not automatically guarantee strong security.**

The effectiveness of password protection depends significantly on the strength and unpredictability of the chosen password.

**2. Hash extraction is an important stage in document password auditing.**

Before attempting password recovery, the relevant verification information must first be extracted in a compatible format.

**3. Hash compatibility matters.**

Password auditing tools must correctly recognise and process the extracted hash. An improperly formatted hash can result in loading errors or unsuccessful execution.

**4. Password recovery is not instantaneous.**

The time required to recover a password depends on its complexity, the attack method, available wordlists, and computational resources.

**5. Multiple tools serve different purposes.**

Hash calculators, extraction utilities, and password recovery tools contribute different stages of the overall password auditing process.

---

## 7. Security Implications and Recommendations

The exercise highlights several important security practices for individuals and organisations.

- Use long, unique, and unpredictable passwords.
- Avoid commonly used passwords and predictable combinations.
- Enable multi-factor authentication wherever supported.
- Use reputable encryption mechanisms when protecting sensitive documents.
- Avoid sharing passwords through insecure communication channels.
- Implement appropriate password management practices.
- Conduct periodic security assessments of password-protected files.

Strong password practices remain an important component of an effective security strategy.

---

## 8. Challenges Encountered

Working with password auditing tools also highlighted some practical considerations:

- Ensuring that extracted hashes were correctly formatted.
- Understanding compatibility between extracted hashes and John the Ripper.
- Configuring the necessary dependencies for hash extraction utilities.
- Interpreting terminal output and identifying hash-loading issues.
- Understanding the relationship between successful hash extraction and actual password recovery.

These challenges reinforced the importance of troubleshooting, tool configuration, and understanding the underlying technical processes.

---

## 9. Learning Outcomes

By completing this exercise, I strengthened my understanding of:

- Document password protection and encryption.
- Cryptographic hashing and hash representation.
- Password hash extraction.
- John the Ripper and its password auditing capabilities.
- Dictionary-based password attacks.
- Password recovery workflows.
- The importance of strong authentication practices.

Most importantly, the exercise provided practical exposure to how password security can be assessed from an attacker's perspective and how these techniques contribute to better defensive security practices.

---

## 10. Evidence and Practical Demonstrations

Screenshots documenting the practical exercise are included below.

### 10.1 Hash Extraction

![Hash Extraction](screenshots/hash-extraction.png)

*Demonstration of extracting password hash information from a protected document.*

### 10.2 NetworkWalks Official Hash Calculator

![Hash Calculator](screenshots/hash-calculator.png)

*Demonstration of cryptographic hash generation and analysis.*

### 10.3 John the Ripper

![John the Ripper](screenshots/john-the-ripper.png)

*Terminal demonstration of hash loading and password auditing using John the Ripper.*

### 10.4 NetworkWalks Password Kcracker

![Password Kcracker](screenshots/password-kcracker.png)

*Practical exploration of password recovery using the NetworkWalks Password Kcracker.*

### 10.5 Password Recovery Results

![Password Recovery Results](screenshots/password-recovery.png)

*Evidence of the password recovery process, where applicable.*

---

## 11. Conclusion

This project provided practical insight into the relationship between document encryption, cryptographic hashing, and password security.

Working with John the Ripper, pdf2john, and the NetworkWalks security tools helped demonstrate the stages involved in assessing password-protected documents, from hash extraction to password auditing and recovery attempts.

Beyond learning how to operate the tools, the exercise strengthened my understanding of password vulnerabilities, hash compatibility, and the importance of implementing stronger authentication and document protection mechanisms.

**Understanding how security mechanisms can be tested is an important step towards understanding how they can be strengthened.**

---

## 12. Ethical Considerations

All activities described in this documentation are intended strictly for educational purposes and authorised security testing.

Password auditing and recovery techniques should only be performed on documents and systems that you own or have explicit permission to assess.

Unauthorised access to protected documents or systems may violate applicable laws and privacy rights.

---

### Project Information

| Field | Details |
|---|---|
| Programme | Cybersecurity Internship |
| Organisation | NetworkWalks |
| Project | Document Password Security & Hash Cracking |
| Week | 3 |
| Primary Tool | John the Ripper |
| Supporting Tools | pdf2john, NetworkWalks Official Hash Calculator, NetworkWalks Password Kcracker |
| Domain | Cybersecurity / Ethical Hacking |

**Author:** Isah Suleiman

**Linkedin:** www.linkedin.com/in/isah-suleiman-0a183a278

**Focus:** Practical Cybersecurity, Ethical Hacking & Security Assessment
