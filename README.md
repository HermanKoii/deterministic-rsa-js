# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA keys using a seeded random number generation process. Unlike traditional RSA key generation methods, this library allows you to reproduce the same key pair consistently given the same input seed.

### Key Features
- 🔑 Deterministic RSA key generation
- 🧮 Supports variable key sizes (minimum 192 bits)
- 🚀 Multithreaded prime generation
- 🔒 Compatible with JSON Web Key (JWK) format
- 🌈 Pure JavaScript implementation

### Use Cases
- Reproducible cryptographic key generation
- Deterministic wallet and identity systems
- Testing and simulation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object with `privateKey` and `publicKey` in JWK format.

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.randomBytes(32);
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // JWK public key
console.log(keyPair.privateKey); // JWK private key
```

### Utility Functions

The library includes internal utility functions for prime generation and modular arithmetic:
- `seededRandPrime`: Generates a prime number from a seed
- `millerRabin`: Probabilistic primality test
- `modExp`: Modular exponentiation
- `gcd`: Greatest common divisor calculation

## Repository Structure

- `index.js`: Main library implementation
- `package.json`: Project metadata and dependencies
- `test.js`: Test suite for the library
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a Pull Request

### Running Tests

```bash
npm test
```

## Performance and Limitations

- Best suited for scenarios requiring reproducible key generation
- Performance depends on key size and hardware
- Probabilistic primality testing means extremely rare chance of generating composite numbers

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

Built with ❤️ using pure JavaScript and inspired by cryptographic best practices.