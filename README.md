# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library for generating deterministic RSA keys using a seed. Unlike traditional RSA key generation methods, this library allows you to reproducibly generate cryptographic key pairs from a consistent seed, making it ideal for scenarios requiring predictable key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌐 Pure JavaScript implementation
- 🧩 Supports configurable key sizes
- 🔒 Uses secure prime generation algorithms
- 🚀 Multithreaded prime number generation
- 📊 Compatible with JSON Web Key (JWK) standard

### Use Cases
- Blockchain and cryptocurrency applications
- Reproducible key generation in distributed systems
- Testing and simulation environments
- Scenarios requiring predictable cryptographic keys

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, e = 65537n)`

Generates deterministic RSA key pairs from a seed.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Public key details
console.log(keyPair.privateKey); // Private key details
```

## Repository Structure
- `index.js`: Main library implementation
- `test.js`: Test suite for library functions
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Running Tests
```bash
npm test
```

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Acknowledgements
- Andre Vallestero (Original Author)
- Inspired by cryptographic key generation techniques