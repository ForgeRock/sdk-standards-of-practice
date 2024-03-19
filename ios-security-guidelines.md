# iOS Security Guideline

## Introduction

This document outlines the security guidelines and best practices for developing iOS Mobile SDK. 
It aims to ensure that all SDKs are developed with the highest security standards to protect company and user data.

## References and Further Reading

* See [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/)
* See [OWASP Mobile Application Security](https://owasp.org/www-project-mobile-app-security/)
* See [Apple Platform Security](https://support.apple.com/en-ca/guide/security/welcome/web)

These documents cover most of the security best practices; below are the key highlights and a summary:


## 1. General Security Principles

### Principle of Least Privilege
Ensure that all system and application components operate with the minimum privileges necessary for their specific roles. This includes restricting access rights for users, accounts, and computing processes to only those resources absolutely required to perform their functions.
### Secure by Design
Incorporate security considerations from the earliest stages of SDK design and architecture. This proactive approach involves identifying potential threats and vulnerabilities early on, allowing for the design of robust security measures that are integral to the application, rather than retrofitted after development.
### Regular Security Audits
Conduct regular security audits of both the SDK and its development environment. These audits should assess compliance with these guidelines, identify security gaps, and recommend enhancements. Audits can be performed internally or by third-party experts specializing in mobile SDK security.
### Secure by Default
The SDK should be configured with secure settings by default, prioritizing security to minimize vulnerabilities. This includes enabling secure communication protocols, enforcing strong encryption, and implementing secure coding practices. The SDK should provide a secure foundation for developers, and any intentional change to lower security should be clearly indicated in the configuration options.


## 2. Development Environment Security

### Secure Storage of Credentials and Secrets
Safeguard all credentials, secrets, and keys used in the development environment. Use secure vaults and password managers to store these items, ensuring they are encrypted and access is restricted to authorized personnel only.
### Use of Trusted Networks
Ensure that development activities occur within a secure, trusted network environment. Employ VPNs and firewalls to protect against unauthorized access and data breaches. Regularly monitor network traffic for suspicious activity that could indicate a security threat.
### Regular Software Updates
Keep the development environment up-to-date with the latest security patches and software updates. This includes the operating systems of development machines, development tools, and any third-party libraries or frameworks used in the SDK development process.
### Protection of Sensitive Information
Do not commit secrets, certificates, keys, or any sensitive information to Git as separate files or hardcoded in comments or values. This helps prevent unauthorized access to sensitive information and reduces the risk of exposure.


## 3. SDK Development Security

### Secure Coding Practices
Adhere to the latest secure coding guidelines provided by Apple.
Use static and dynamic analysis tools to identify and fix security vulnerabilities.

### Trust No One Policy
Adopt a "trust no one" policy, treating all data as potentially malicious, even if it originates from your own server.
Ensure that all rendered strings undergo strict validation and escaping logic before being used to prevent potential security vulnerabilities.

### Data Encryption
Encrypt sensitive data both at rest and in transit using strong encryption algorithms.
Utilize Apple's built-in encryption frameworks, like Data Protection API for data at rest and Transport Layer Security (TLS) for data in transit.
Use CryptoKit (iOS13+) for performing cryptographic operations in a secure and efficient manner.
### Secure Communication
Ensure all data transmitted between the SDK and servers is over HTTPS using TLS 1.2 or higher.
Implement certificate and public key pinning to mitigate the risk of man-in-the-middle (MITM) attacks.
### Error Handling and Logging
Properly handle errors and exceptions without exposing sensitive information or system details to the users.
Log security-relevant events in a format that supports monitoring and analysis, but ensure logs do not contain sensitive information.
### Dependency Management
Regularly review and update the third-party libraries and dependencies to their latest secure versions.
Perform security assessment of third-party components before integrating them into the SDK.


## 4. Data Storage and Privacy

### Data at Rest Security
Use the iOS Keychain to store sensitive information like tokens, credentials, and personal data securely.
Enable File Data Protection to add additional layers of encryption to files stored on the device.
Do not store sensitive information in UserDefaults or plain files.
Use Secure Enclave for generating and storing cryptographic keys
### Data in Transit Security
Use App Transport Security (ATS) to enforce secure network connections.
Encrypt sensitive data using strong encryption algorithms before transmitting.
### Privacy Policies Compliance
Ensure the SDK complies with global privacy regulations such as GDPR and CCPA as a minimum requirement.
Implement necessary features for data access, rectification, and deletion requests by users.


## 5. Third-party Services and Libraries

### Security Assessment of Third-party Services
Conduct thorough security assessments of all third-party services and APIs before integration.
Review the security posture and privacy policies of third-party services to ensure they meet our organization's standards.
### Regular Updates and Patch Management
Keep third-party libraries and services updated to their latest versions to mitigate known vulnerabilities.
Establish a process for monitoring and applying security patches and updates in a timely manner.
### Minimal Use
Minimize the use of third-party dependencies to reduce the attack surface. When possible, use native Apple frameworks and libraries that are regularly updated for security.
### Privately Managed Packages
Do not use privately managed packages, especially those maintained by a single individual. Instead, prioritize packages maintained by reputable companies or organizations, as they typically adhere to better security practices and provide reliable support.


## 6. Authentication and Authorization

### Biometric Authentication
Leverage Face ID and Touch ID for secure and user-friendly authentication. Ensure your SDK provides the necessary callbacks to the host application for handling authentication failures or fallbacks.
### OAuth 2.0 and OpenID Connect
For SDKs requiring user authentication, support industry-standard protocols like OAuth 2.0 and OpenID Connect to securely manage user sessions and access tokens.


## 7. Documentation and Developer Guidance

### Secure Usage Guidelines 
Provide clear documentation on how to securely integrate and configure your SDK. Include best practices and common pitfalls to avoid.
### Security Disclosure Policy
Establish a responsible disclosure policy for reporting security vulnerabilities found in your SDK. Encourage the developer community to report potential security issues.

## 8. Automation and Continuous Integration

### Security Testing
Conduct regular security assessments, including penetration testing, to identify and mitigate vulnerabilities.
Incorporate security testing into the CI/CD pipeline for ongoing security assurance.
Implement automated security gates using tools like Checkmarx and Mend to detect issues before merging code.
Intentionally try to break your own implementation and implement tests that cover any discoveries.
### Secure Configuration Management
Ensure that the configuration files used in the CI/CD pipeline are securely managed and protected. Use encryption and access controls to prevent unauthorized access or tampering of sensitive configuration data.


## Security provider services and software
* [Checkmarx](https://checkmarx.com/)
* [Mend](https://www.mend.io/)
* [Sonatype](https://www.sonatype.com/products/vulnerability-scanner)
* [NetSPI](https://www.netspi.com/) for penetration testing.
* [Veracode](https://www.veracode.com/)
* [snyk](https://snyk.io/)
