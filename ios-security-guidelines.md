# iOS Security Guideline

## Introduction

This will be an extension of the [General Security Guidelines](general-security-guidelines.md). Please read that document first.

### Secure Coding Practices
Adhere to the latest secure coding guidelines provided by Apple.

### Data Encryption
Utilize Apple's built-in encryption frameworks, like Data Protection API for data at rest and Transport Layer Security (TLS) for data in transit.
Use CryptoKit (iOS13+) for performing cryptographic operations in a secure and efficient manner.

### Data at Rest Security
Use the iOS Keychain to store sensitive information like tokens, credentials, and personal data securely.
Enable File Data Protection to add additional layers of encryption to files stored on the device.
Do not store sensitive information in UserDefaults or plain files.
Use Secure Enclave for generating and storing cryptographic keys

### Minimal Use of Third-party Dependencies
Favor native Apple frameworks and libraries to minimize the attack surface and leverage the security updates provided by Apple.

### Secure Usage Guidelines 
Provide documentation on securely integrating and configuring the iOS SDK, highlighting best practices and common pitfalls specific to iOS development.

### Biometric Authentication
Leverage Face ID and Touch ID for secure and user-friendly authentication. 

### Security Testing 
Integrate security testing in the CI/CD pipeline, focusing on iOS-specific security assessments and using tools compatible with iOS development environments.

