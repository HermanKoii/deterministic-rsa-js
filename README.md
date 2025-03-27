# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA key pairs with precision and predictability. This library provides cryptographically secure RSA key generation using seeded pseudo-random number generation, enabling reproducible key creation for specific cryptographic and blockchain applications.

### Key Features
- 🔒 Deterministic RSA key generation
- 💻 Supports both Node.js and browser environments
- 🧮 Configurable key bit lengths
- 🚀 Multi-threaded prime generation
- 📊 Customizable public encryption exponent
- 🔍 Rigorous primality testing with Miller-Rabin algorithm

### Why Use Deterministic RSA?
Traditional RSA key generation relies on randomness, which makes key reproduction impossible. This library solves that by allowing key regeneration from a consistent seed, crucial for:
- Blockchain and distributed systems
- Reproducible cryptographic protocols
- Deterministic wallet generation
- Predictable key infrastructure

## Installation

Install via npm:
```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js 14.0.0 or higher
- JavaScript environment supporting BigInt

## API Reference

### `rsaGenKeys(bits, seed, [exponent])`

Generates deterministic RSA key pair.

#### Parameters
- `bits` (number): Total RSA key modulus size (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `exponent` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
Promise resolving to an object with:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Corresponding public RSA key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = new Uint8Array(32).fill(1);  // Example seed
rsaGenKeys(2048, seed).then(keys => {
  console.log(keys.publicKey);
  console.log(keys.privateKey);
});
```

## Repository Structure
- `index.js`: Core library implementation
- `test.js`: Unit and integration tests
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license details

## Contributing

### Guidelines
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### Running Tests
```bash
npm test
```

## Performance Notes
- Prime generation is multi-threaded using `workerpool`
- Uses optimized Miller-Rabin primality testing
- Implemented with native BigInt for large number handling

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Security
While designed with cryptographic rigor, always have critical systems independently audited. Use at your own discretion.

## Acknowledgments
Inspired by cryptographic standards and implementations from digital security research.