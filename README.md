# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library for generating deterministic RSA keys using a seed-based approach. Unlike traditional RSA key generation methods, this library allows reproducible key generation from a consistent seed, making it ideal for scenarios requiring predictable cryptographic key creation.

### Key Features
- 🔒 Deterministic RSA key generation
- 🌐 Pure JavaScript implementation
- 💻 Supports multithreaded prime generation
- 🔑 Generates JWK (JSON Web Key) formatted public and private keys
- ⚙️ Configurable key bit sizes
- 🔬 Implements Miller-Rabin primality testing

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### Key Generation Function

#### `rsaGenKeys(bits, seed, e = 65537n)`

Generates RSA key pairs deterministically based on input parameters.

**Parameters:**
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic prime generation
- `e` (BigInt, optional): Public encryption exponent (default: 65537)

**Returns:**
An object containing `privateKey` and `publicKey` in JWK format.

**Example Usage:**
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate 2048-bit RSA keys
const seed = crypto.randomBytes(32);
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

### Configuration Notes
- Key sizes must be multiples of 32
- Minimum key size is 192 bits
- Seed must be at least 32 bytes long
- Uses 65537 as the default public exponent (recommended for RSA)

## Repository Structure
- `index.js`: Core library implementation
- `test.js`: Library test suite
- `package.json`: Project configuration and dependencies

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### Running Tests
To run tests, use:
```bash
npm test
```

## Performance & Limitations

- Prime generation uses multithreading via `workerpool`
- Deterministic generation ensures reproducible keys
- Suitable for specialized cryptographic applications
- Not recommended for general-purpose secure key generation

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Dependencies
- `workerpool`: For multithreaded prime generation

## Acknowledgements
Inspired by cryptographic techniques in digital signature and blockchain technologies.