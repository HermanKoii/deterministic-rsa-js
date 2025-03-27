# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA key pairs using seeded random number generation. This library allows developers to create reproducible RSA keys with precise control over key generation, making it ideal for cryptographic applications requiring predictable key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌱 Seeded prime number generation
- 🔢 Configurable key size (192+ bits)
- ⚡ Multi-threaded prime generation
- 📦 JSON Web Key (JWK) compatible output
- 🔬 Advanced prime number validation

### Why Use Deterministic RSA?
- Predictable key generation for testing and simulation
- Reproducible cryptographic scenarios
- Controlled randomness in key creation
- Consistent key pair generation across environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, e = 65537n)`

Generates a deterministic RSA key pair from a seed.

#### Parameters
- `bits` (number): Total key size (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two properties:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project configuration
- `LICENSE`: MIT license details

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Run tests
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance Considerations
- Uses multi-threaded prime generation
- Implements optimized Miller-Rabin primality testing
- Efficient modular arithmetic algorithms

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Dependencies
- `workerpool`: For multi-threaded prime generation

## Disclaimer
This library is in beta. Use in production environments with caution and thorough testing.