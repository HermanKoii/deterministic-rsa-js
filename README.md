# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA key pairs from seeds. This library provides a unique capability to reproducibly generate RSA cryptographic keys using a predefined seed, which is crucial for scenarios requiring consistent key generation across different environments.

### Key Features
- 🔐 Deterministic RSA Key Generation
- 🧮 Multithreaded Prime Number Generation
- 📊 Configurable Key Size (192+ bits)
- 🔬 Probabilistic Primality Testing
- 🔑 JSON Web Key (JWK) Formatted Output

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and distributed systems
- Testing and simulation environments
- Scenarios requiring predictable key generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js (version 14.0.0 or higher)
- Modern JavaScript environment supporting BigInt

## API Reference

### `rsaGenKeys(bits, seed[, e])`

Generates deterministic RSA key pairs.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object containing:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license details

## Contributing

### Contributing Guidelines
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to your branch
5. Create a pull request

### Running Tests
```bash
npm test
```

## Performance and Limitations

- Key generation is computationally intensive
- Supports key sizes from 192 to 4096 bits
- Uses probabilistic primality testing

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Built with ❤️ by [@open-koi](https://github.com/open-koi)
- Uses `workerpool` for multithreaded prime generation