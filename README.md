# Deterministic RSA JS 🔐

## Project Overview

Deterministic RSA JS is a lightweight, pure JavaScript library for generating deterministic RSA keys using a provided seed. Unlike traditional RSA key generation, this library allows you to reproducibly generate RSA key pairs from a consistent input seed.

### Key Features
- 🔢 Deterministic RSA key generation
- 🚀 Uses multithreaded prime generation
- 🔒 Supports configurable key sizes
- 📦 Outputs keys in JSON Web Key (JWK) format
- 🧮 Implements custom seeded random number generation
- 🔍 Includes Miller-Rabin primality testing

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and cryptocurrency applications
- Deterministic wallet key generation
- Testing and simulation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js (version 12 or higher recommended)
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates deterministic RSA key pairs.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public exponent, defaults to 65537n

#### Returns
An object with `privateKey` and `publicKey`, both in JWK format.

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
- `package.json`: Project metadata and dependencies
- `test.js`: (Optional) Test suite for the library
- `LICENSE`: MIT license details

## Contributing

### How to Contribute
1. Fork the repository
2. Create a new branch for your feature
3. Make your changes
4. Write or update tests
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance Considerations
- Key generation is computationally intensive
- Uses workerpool for multithreaded prime generation
- Seed quality significantly impacts key generation

## Security
- Always use cryptographically secure random seeds
- Validate and sanitize inputs
- Consider additional security measures for production use

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Support and Community

For issues, questions, or discussions, please use the GitHub Issues section.

---

*Crafted with ❤️ by Andre Vallestero and the Open Koi community*