# Deterministic RSA Key Generation Library

## Project Overview

`deterministic-rsa-js` is a powerful JavaScript library for generating deterministic RSA keys using a seeded approach. This library provides a robust solution for cryptographic key generation with the following key features:

- 🔐 Deterministic RSA key generation
- 🧮 Precise control over key bit length
- 🚀 Multithreaded prime number generation
- 💻 Pure JavaScript implementation
- 🔬 Cryptographically secure prime generation algorithms

### Why Deterministic RSA?

Traditional RSA key generation is non-deterministic, meaning each key generation produces different results. This library solves that by allowing reproducible key generation from a consistent seed, which is crucial for:

- Predictable key generation in testing environments
- Blockchain and distributed systems
- Cryptographic protocols requiring reproducible keys

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites

- Node.js version 14.0.0 or higher
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (optional BigInt): Public exponent, defaults to 65537n

#### Returns
An object containing:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Corresponding public RSA key

#### Example Usage

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

### Internal Functions (Advanced Usage)

While primarily internal, these functions are exposed for advanced use:

- `seededRandPrime(bits, seed, exp, smallPrimes)`: Generate a seeded prime number
- `millerRabin(n, k)`: Probabilistic primality test
- `modExp(a, b, n)`: Modular exponentiation
- `biToB64url(num)`: BigInt to Base64URL conversion

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Test suite for the library
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvements`)
3. Make your changes
4. Run tests to ensure everything works
5. Submit a pull request

### Running Tests

```bash
npm test
```

## Performance Considerations

- Uses multithreading via `workerpool` for parallel prime generation
- Implements efficient algorithms like Miller-Rabin for prime testing
- Optimized for modern JavaScript engines

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

While this library provides robust key generation, always consult cryptography experts for security-critical applications.