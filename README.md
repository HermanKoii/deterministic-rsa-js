# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library that provides deterministic RSA key generation using pure JavaScript. Unlike traditional RSA key generation, which produces random keys, this library allows developers to generate reproducible RSA key pairs from a consistent seed, enabling precise key reconstruction and advanced cryptographic workflows.

### Key Features
- 🔑 Deterministic RSA key generation
- 🧮 Pure JavaScript implementation
- 🔒 Supports multiple key bit lengths
- 🚀 Multithreaded prime generation
- 🔍 Comprehensive primality testing

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and distributed systems
- Consistent key derivation across different platforms
- Testing and simulation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js v12 or higher
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair from a provided seed.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object containing `privateKey` and `publicKey` in JSON Web Key (JWK) format.

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Public JWK
console.log(keyPair.privateKey); // Private JWK
```

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Unit tests and examples
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT License details

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Commit your changes
4. Push to your branch
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance Considerations
- Uses multithreaded prime generation
- Implements efficient modular arithmetic
- Miller-Rabin primality testing with adaptive rounds

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer
This library is in beta. Use in production environments with caution and thorough testing.