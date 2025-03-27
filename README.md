# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library for generating deterministic RSA key pairs using a seeded approach. Unlike traditional RSA key generation methods that rely on random number generation, this library allows you to generate reproducible RSA keys from a consistent seed.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌐 Pure JavaScript implementation
- 🔒 Supports configurable key sizes
- 🧵 Multithreaded prime generation
- 📊 Compliant with JSON Web Key (JWK) standard

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and cryptocurrency applications
- Secure key derivation in distributed systems
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
- `bits` (number): Total number of bits in the RSA modulus. Must be:
  - A multiple of 32
  - At least 192 bits
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public exponent. Defaults to 65537n.

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Corresponding public RSA key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = new Uint8Array(32).fill(0); // Your seed here
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure

- `index.js`: Main library implementation
- `package.json`: Project metadata and dependencies
- `test.js`: Test suite for library functions
- `LICENSE`: MIT license details

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes and commit them
4. Push to the branch: `git push origin feature/your-feature`
5. Submit a pull request

### Running Tests

To run tests:

```bash
npm test
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Performance Considerations

- The library uses multithreaded prime generation for efficiency
- Deterministic generation may be slightly slower than purely random methods
- Recommended for scenarios where key reproducibility is crucial

## Security Notes

- Always use cryptographically secure seeds
- Validate and protect your seed values
- For production use, consider additional security measures

## Acknowledgements

Inspired by cryptographic techniques in blockchain and distributed systems.