# Deterministic RSA.js 🔐

## Project Overview

Deterministic RSA.js is a specialized JavaScript library for generating deterministic RSA keys using a seeded pseudo-random number generation process. Unlike traditional RSA key generation methods, this library allows you to predictably generate RSA key pairs from a consistent 32-byte seed.

### Key Features
- 🎲 Deterministic key generation from a seed
- 🔒 Cryptographically secure prime number generation
- 🧵 Multithreaded prime generation using `workerpool`
- 📊 Configurable key size (minimum 192 bits)
- 🔑 JSON Web Key (JWK) compatible output
- 🛡️ Miller-Rabin primality testing
- 🚀 Pure JavaScript implementation

### Use Cases
- Reproducible key generation for testing
- Consistent key derivation in blockchain and distributed systems
- Scenarios requiring predictable cryptographic key creation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js (version 12.0.0 or higher)
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete RSA private key
- `publicKey` (JsonWebKey): RSA public key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Unit and integration tests
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT License details

## Contributing

### How to Contribute
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

## Performance and Limitations

- Key generation can be computationally intensive
- Designed for specific use cases requiring deterministic keys
- Not recommended for high-frequency cryptographic operations

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for complete details.

## Credits

Developed by Andre Vallestero as part of the Open Koi project.