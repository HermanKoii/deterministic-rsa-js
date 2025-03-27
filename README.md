# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight, vanilla JavaScript library for generating deterministic RSA keys. Unlike traditional RSA key generation methods, this library allows you to generate reproducible RSA key pairs from a seed, making it perfect for scenarios requiring predictable key generation.

### Key Features
- Deterministic RSA key generation
- Uses a 32-byte seed for reproducible key generation
- Supports configurable key bit lengths
- Multithreaded prime generation
- JSON Web Key (JWK) format output
- Uses Miller-Rabin primality testing
- Low external dependencies

### Use Cases
- Blockchain and cryptocurrency applications
- Reproducible key generation in distributed systems
- Testing and development scenarios
- Cryptographic protocols requiring deterministic keys

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total bit length of the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Create a 2048-bit key with a specific seed
const seed = new Uint8Array(32).fill(42);  // Example seed
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Make your changes
4. Run tests: `npm test`
5. Submit a pull request

## Performance and Limitations

- Key generation can be computationally intensive
- Recommended for controlled, predictable environments
- Not suitable for cryptographically secure random key generation

## Dependencies

- `workerpool`: For multithreaded prime generation

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Disclaimer

This library is for educational and specific use cases. Always consult cryptography experts for security-critical applications.