# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library for generating deterministic RSA key pairs using a seeded approach. Unlike traditional RSA key generation methods, this library allows reproducible key generation from a consistent 32-byte seed, which is crucial for scenarios requiring verifiable and repeatable cryptographic key generation.

### Key Features
- 🔑 Deterministic RSA key pair generation
- 🌱 Seed-based key derivation
- 🚀 Multithreaded prime generation
- 🔒 Configurable key bit lengths
- ✅ Built-in primality testing

### Use Cases
- Cryptographic simulations
- Reproducible testing environments
- Blockchain and distributed systems
- Deterministic wallet generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates deterministic RSA key pairs from a seed.

#### Parameters
- `bits` (number): Total bit length of the RSA modulus (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (optional, BigInt): Public encryption exponent (default: 65537)

#### Returns
An object containing `privateKey` and `publicKey` in JSON Web Key (JWK) format.

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.randomBytes(32);
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.privateKey);
console.log(keyPair.publicKey);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Test suite for library verification
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Run tests: `npm test`
5. Commit your changes
6. Push to the branch
7. Create a Pull Request

## Performance Considerations

- Uses multithreaded prime generation
- Implements efficient primality testing (Miller-Rabin)
- Optimized modular arithmetic operations

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Dependencies

- `workerpool`: For multithreaded prime generation

## Disclaimer

This library is for educational and developmental purposes. Always consult cryptography experts for production-grade security implementations.