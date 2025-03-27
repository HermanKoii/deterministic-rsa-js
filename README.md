# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA keys using seeded randomness. Unlike traditional RSA key generation methods, this library allows you to reproducibly generate RSA key pairs from a consistent seed input.

### Key Features
- 🔐 Deterministic RSA key generation
- 🧩 Supports configurable key bit lengths
- 🚀 Multithreaded prime number generation
- 🌐 Compatible with JSON Web Key (JWK) format
- 💻 Pure JavaScript implementation

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and distributed systems
- Testing and simulation environments
- Cryptographic protocols requiring predictable keys

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js version 14.0.0 or higher
- `workerpool` library (included as a dependency)

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key
  - Must be a multiple of 32
  - Minimum 192 bits
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object with two properties:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

### Internal Utility Functions

The library also includes several internal utility functions used during key generation:

- `seededRandPrime(bits, seed, exp, small_primes)`: Generates a seeded random prime
- `millerRabin(n, k)`: Primality testing
- `modExp(a, b, n)`: Modular exponentiation
- `gcd(a, b)`: Greatest common divisor calculation
- `modInverse(exp, phi)`: Modular multiplicative inverse
- `biToB64url(num)`: BigInt to Base64URL conversion

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch for your feature
3. Commit your changes
4. Create a pull request

### Running Tests
```bash
npm test
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Performance Note

The library uses multithreading via `workerpool` and implements optimized algorithms for prime generation and modular arithmetic.

## Security

While designed with cryptographic best practices, always have critical implementations professionally audited. This library is intended for research and specific use cases.