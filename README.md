# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library that enables deterministic generation of RSA cryptographic keys from seed values. Unlike traditional RSA key generation, this library allows you to reproducibly generate RSA key pairs using a consistent 32-byte seed.

### Key Features
- 🔐 Deterministic RSA key generation
- 🌐 Pure JavaScript implementation
- 🚀 Supports configurable key bit lengths
- 💻 Multithreaded prime generation
- 🔢 Uses Miller-Rabin primality testing
- 📊 Works with standard JsonWebKey (JWK) format
- 🔬 Cryptographically secure random number generation

### Use Cases
- Reproducible key generation for testing
- Blockchain and cryptocurrency applications
- Deterministic wallet key derivation
- Consistent cryptographic key generation in distributed systems

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js version 12.0 or higher
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537

#### Returns
An object with `privateKey` and `publicKey`, both in JsonWebKey (JWK) format.

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit RSA key pair
const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Prints the public key
console.log(keyPair.privateKey); // Prints the private key
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Unit tests for library functions
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Commit your changes
4. Push to your branch
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance Considerations

- Key generation is computationally intensive
- Uses Web Workers for multithreaded prime generation
- Performance varies with key bit length

## Security

This library uses cryptographically secure techniques:
- Miller-Rabin primality testing
- Seeded pseudo-random number generation
- Coprime and primality checks

However, always consult a security expert for critical applications.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

While designed with care, this library is primarily intended for educational and experimental purposes. Always use well-established cryptographic libraries for production security-critical applications.