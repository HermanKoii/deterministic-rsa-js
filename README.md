# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight, pure JavaScript library for generating deterministic RSA keys. Unlike traditional RSA key generation methods that produce random keys, this library allows you to generate reproducible RSA key pairs using a seed, making it ideal for scenarios requiring consistent cryptographic key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌐 Pure JavaScript implementation
- 🔒 Supports customizable key sizes
- 🚀 Multithreaded prime number generation
- 📋 Returns keys in JSON Web Key (JWK) format

### Key Benefits
- Reproducible cryptographic keys
- Suitable for blockchain, distributed systems, and testing environments
- No external dependencies for core functionality

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits in the RSA modulus. Must be:
  - A multiple of 32
  - At least 192 bits
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent. Defaults to 65537n.

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit RSA key pair
const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Public key
console.log(keyPair.privateKey); // Private key
```

## Repository Structure
- `index.js`: Core library implementation
- `test.js`: Test suite for library functionality
- `package.json`: Project metadata and dependencies

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/awesome-improvement`)
3. Commit your changes (`git commit -am 'Add awesome improvement'`)
4. Push to the branch (`git push origin feature/awesome-improvement`)
5. Create a Pull Request

### Running Tests
```bash
npm test
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Performance Notes

- Uses multithreaded prime generation for efficiency
- Implements Miller-Rabin primality testing
- Provides deterministic key generation with minimal entropy requirements