# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library that provides deterministic RSA key generation using pure JavaScript. Unlike traditional RSA key generation methods that rely on random number generation, this library enables reproducible RSA key pair creation from a consistent seed.

### Key Features
- 🔐 Deterministic RSA key generation
- 🧮 Supports configurable key bit lengths
- 🚀 Multithreaded prime number generation
- 🔢 Works with standard JSON Web Key (JWK) format
- 💻 Pure JavaScript implementation
- 🌐 Works in both Node.js and browser environments

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and cryptocurrency applications
- Secure, predictable key creation for distributed systems
- Testing and development scenarios requiring consistent key pairs

## Installation

You can install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js version 12 or higher
- Basic understanding of RSA cryptography

## API Reference

### `rsaGenKeys(bits, seed, [e = 65537n])`

Generates a deterministic RSA key pair from a given seed.

#### Parameters
- `bits` (number): Total bit length of the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537

#### Returns
An object containing:
- `privateKey` (JsonWebKey): Complete private key in JWK format
- `publicKey` (JsonWebKey): Public key in JWK format

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

async function generateKeys() {
  const seed = crypto.getRandomValues(new Uint8Array(32));
  const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
  console.log(privateKey, publicKey);
}
```

### Key Generation Constraints
- Supported key sizes: 192 bits and above (multiples of 32)
- Seed must be a 32-byte Uint8Array
- Uses Miller-Rabin primality testing for prime generation
- Configurable public exponent (default: 65537)

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Unit tests
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Implement your changes
4. Write or update tests
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance and Security Notes
- Prime generation uses multithreading for efficiency
- Implements cryptographically secure seeded random number generation
- Follows standard RSA key generation best practices

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer
This library is intended for educational and development purposes. For production cryptographic needs, always consult with security experts and use well-audited cryptographic libraries.