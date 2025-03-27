# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight, pure JavaScript library for generating deterministic RSA keys. Unlike traditional RSA key generation methods that rely on random number generation, this library allows you to generate RSA key pairs from a consistent seed, ensuring reproducible cryptographic key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🧮 Uses seeded randomness for predictable key creation
- 💻 Pure JavaScript implementation
- 🚀 Supports multithreaded prime number generation
- 🔒 Compliant with JSON Web Key (JWK) standard
- 📊 Configurable key size (192+ bits, multiple of 32)

### Use Cases
- Reproducible key generation for testing
- Blockchain and cryptocurrency applications
- Deterministic cryptographic systems
- Scenarios requiring predictable key generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js (version 12 or higher)
- Supports both browser and Node.js environments

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total bit length of the RSA key (minimum 192, must be multiple of 32)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete RSA private key
- `publicKey` (JsonWebKey): Corresponding RSA public key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Create a 2048-bit key with a specific seed
const seed = new Uint8Array(32).fill(123);  // Example seed
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Unit tests and examples
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Run tests: `npm test`
5. Submit a pull request

### Running Tests
Currently, manual testing is recommended. Future versions will include automated test scripts.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

This library is in beta. Use in production environments with caution and thorough testing.