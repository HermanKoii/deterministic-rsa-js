# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library that provides deterministic RSA key generation using a seed-based approach. Unlike traditional random key generation, this library allows you to generate reproducible RSA key pairs from a consistent seed, which is critical for scenarios requiring predictable cryptographic key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🧩 Supports configurable key sizes
- 🚀 Multithreaded prime number generation
- ✅ Fully compliant with JSON Web Key (JWK) standard
- 🔬 Comprehensive primality testing
- 📦 Lightweight and dependency-minimal

### Use Cases
- Reproducible key generation for testing
- Blockchain and cryptocurrency applications
- Cryptographic systems requiring predictable key generation
- Distributed key management systems

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates deterministic RSA key pairs.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537

#### Returns
An object containing:
- `privateKey`: Complete JWK private key
- `publicKey`: JWK public key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.randomBytes(32);
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

### Key Generation Constraints
- Minimum key size: 192 bits
- Key size must be a multiple of 32
- Seed must be at least 32 bytes long

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request

### Running Tests
To run tests, use:
```bash
npm test
```

## Performance Considerations

- Uses multithreaded prime generation
- Implements efficient primality testing
- Minimal external dependencies

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

Developed by Andre Vallestero