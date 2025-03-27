# Deterministic RSA.js

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library designed to generate RSA cryptographic key pairs deterministically from seed values. Unlike traditional random key generation, this library allows you to reproducibly create RSA keys, which can be crucial for scenarios requiring consistent key derivation.

### Key Features
- 🔐 Deterministic RSA key generation
- 🧮 Supports configurable key sizes (minimum 192 bits)
- 🚀 Multi-threaded prime number generation
- 🔢 Supports custom public exponent
- 📦 Generates keys in standard JSON Web Key (JWK) format
- 💻 Works in Node.js and modern browsers

### Use Cases
- Cryptographic systems requiring reproducible key generation
- Blockchain and distributed systems
- Testing and simulation environments
- Scenarios where key derivation from a seed is essential

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e = 65537n])`

Generates a deterministic RSA key pair from a provided seed.

**Parameters:**
- `bits` (number): Total key size, must be a multiple of 32 and ≥ 192
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (optional BigInt): Public encryption exponent, defaults to 65537

**Returns:**
An object with two keys: 
- `privateKey`: JWK format private key
- `publicKey`: JWK format public key

**Example:**
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

### Internal Utility Functions
- `seededRandPrime()`: Generates prime numbers using a seeded random algorithm
- `millerRabin()`: Probabilistic primality testing
- `modExp()`: Modular exponentiation implementation
- `gcd()`: Greatest common divisor calculation
- `modInverse()`: Modular multiplicative inverse calculation

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Test suite for library functionality
- `package.json`: Project configuration and dependencies
- `LICENSE`: MIT license details

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### Running Tests
```bash
npm test
```

## Performance and Limitations

- Prime generation is multi-threaded for improved performance
- Recommended for use cases tolerating slight performance overhead
- Not recommended for high-frequency key generation

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Dependencies
- `workerpool`: Used for multi-threaded prime generation