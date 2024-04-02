# Security Guidelines - Android

## Introduction

This Guideline aim to offer industrial best practice recommendations for developers to build a secure native 
Android Mobile SDK. While there are excellent security guidelines available from Android's official documentation, 
it is highly recommended to thoroughly review these documents. 
This guideline will primarily focus on enhancing the security of SDK development

## Security Guideline

* See [OWASP Top 10](https://owasp.org/www-project-mobile-top-10/)
* See [Android Security Guidelines](https://developer.android.com/privacy-and-security/security-tips)

Above documents include most of the security best practice, here are the highlight and summary:

| Category                                                                     | Best Practice                                                                                                                                                  |
|------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exported Component (Activity, Service, Content Provider, Broadcast Receiver) | - Mark ```android:exported = "false"```<br/> - Restrict components with signature based permission.                                                            |
| Data Encryption                                                              | Sensitive data should be encrypted with key generated with AndroidKeyStore                                                                                     |
| Sensitive information disclosure                                             | - Sensitive data (e.g token, password, username, PII, Payment) should not be logged.<br/> - Ensure data are encrypt in transit or storage.<br/>                |
| Transport Layer Security                                                     | Always use HTTPS instead of HTTP.                                                                                                                              |
| Weak Hashing Algorithm                                                       | Avoid using MD5 and SHA-1 hashing.                                                                                                                             |
| Data Storage                                                                 | Store data securely, for example use [EncryptedSharedPreferences](https://developer.android.com/reference/androidx/security/crypto/EncryptedSharedPreferences) |
| Security scanning & testing                                                  | Integrity with vulnerability scanner and pentration testing, to address security vulnerabilities early in development lifecycle.                               |
| Insecure Data Caching                                                        | Avoid caching sensitive data, e.g authenticate tokens, password.                                                                                               |
| Insecure Cloud Storage                                                       | Avoid cloud backup ```android:allowBackup = "false"```                                                                                                         |
| Deprecated Interface                                                         | Avoid using deprecated class and method.                                                                                                                       |
| 3rd Party Library                                                            | Ensure 3rd party library are secure and up to date.                                                                                                            |
| Store API Key                                                                | Avoid storing API key or credential in the code or file.                                                                                                       |
| Least Privilege                                                              | Request only permissions that the module needs.                                                                                                                |

## Use security provider service and software
* [Checkmarx](https://checkmarx.com/)
* [Mend](https://www.mend.io/)
* [Sonatype](https://www.sonatype.com/products/vulnerability-scanner)
* [NetSPI](https://www.netspi.com/) for penetration testing.