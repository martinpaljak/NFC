# There's NO NEED FOR AN APP, for that!
People love contactless services because they are convenient and easy to use - think about public transit tickets or paying with a contactless payment card (or [wearable](https://fidesmo.com/consumer/wearables/)).

As a user I'm always looking for seamless and ubiquitious experiences that "Just Work (tm)". Solutions that allow me to engage with the environment in useful and convenient ways. Why download yet another app from the appstore silos for simple tasks? Even worse is a requirement to sign up with e-mail addresses and passwords.

JavaCardPro NFC suite (MagicNFC) is the convergence of mobile web and physical world (NFC tags), underlined by modern PKI based security. Usable with the most ubiquitious computing platform - smartphones. Without requiring any extra apps.

Technically: MagicNFC provides a JavaCard application with the AID of `D2760000850101` that implements a [NFC Forum Type 4 tag](https://nfc-forum.org/build/specifications) with a NDEF payload of a dynamic URL.

## Authenticated tap

Unlike some similar proprietary solutions, Authenticated taps use well established, developer-friendly and modern web based technologies:
- [RFC 7517](https://www.rfc-editor.org/rfc/rfc7517): JSON Web Key (JWK)
- [RFC 7638](https://www.rfc-editor.org/rfc/rfc7638): JSON Web Key (JWK) Thumbprint
- [RFC 7515](https://www.rfc-editor.org/rfc/rfc7515): JSON Web Signature (JWS)

![MagicNFC URL](https://github.com/martinpaljak/NFC/blob/645d0221b34a34299daa90e06a5687e6a8aea54a/images/MagicNFC%20URL.png)
Elements of the URL:
- Your free-form base URL, with or without existing GET query parameters
- `v` - version of the Authenticated tap URL. Version 1 is P-256 with R||S signature, Version
- `i` - JWK Thumbprint of the public key used to sign the URL. This is the identity of the MagicNFC device
- `c` - base64url encoded `uint32` counter, increased on every tap
- `s` - JWS compatible ECDSA signature of the whole URL, up to and including the `s=`


### Specifications
| Supported algorithms | Protocol Version |
|----------------------|-----------|
| NIST P-256 | 1, signature is R and S concatenated |
| Secp256k1 Koblitz "Bitcoin curve" | 2, signature is DER encoded |

Java backend library and JavaScript library for web developers included.

# Variations
