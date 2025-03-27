# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight, pure JavaScript library for generating deterministic RSA key pairs. Unlike traditional RSA key generation methods that produce random keys, this library allows you to generate reproducible RSA keys using a cryptographic seed.

### Key Features
- 🔑 Deterministic RSA key generation
- 🧮 Supports configurable key sizes (minimum 192 bits)
- 🔒 Generates standard JSON Web Key (JWK) format keys
- 🚀 Uses multithreaded prime number generation
- 🌐 Pure JavaScript implementation with no external cryptographic dependencies

### Use Cases
- Reproducible key generation for testing
- Consistent key derivation in blockchain and distributed systems
- Scenarios requiring predictable cryptographic key generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js (version 12 or higher)
- `workerpool` package (automatically installed as a dependency)

## API Reference

### `rsaGenKeys(bits, seed, [e = 65537n])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total key size (must be multiple of 32, minimum 192)
  - Example: 2048, 4096
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public encryption exponent (default: 65537)

#### Returns
An object with two properties:
- `privateKey` (JsonWebKey): RSA private key in JWK format
- `publicKey` (JsonWebKey): RSA public key in JWK format

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Public key details
console.log(keyPair.privateKey); // Private key details
```

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project configuration and dependencies
- `LICENSE`: MIT License file

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch for your feature
3. Implement your changes
4. Write or update tests
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance Considerations
- Key generation uses multithreaded prime generation
- Implements efficient algorithms for prime testing and modular arithmetic
- Seed-based generation provides consistent, reproducible results

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer
This library is for educational and specific use cases. For production cryptographic needs, always consult security experts and use well-audited cryptographic libraries.