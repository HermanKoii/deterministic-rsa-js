# Deterministic RSA JS

## Project Overview

**Deterministic RSA JS** is a lightweight JavaScript library for deterministically generating RSA key pairs using a secure, seeded random number generation process. This library provides a unique approach to RSA key generation that allows reproducible key creation based on a seed, which is crucial for specific cryptographic and blockchain applications.

### Key Features
- 🔐 Deterministic RSA key generation
- 🧮 Supports configurable key sizes (minimum 192 bits)
- 🚀 Multithreaded prime generation using `workerpool`
- 🔢 Miller-Rabin primality testing
- 📦 Outputs JSON Web Key (JWK) formatted keys
- 💻 Pure JavaScript implementation

### Use Cases
- Blockchain and cryptocurrency key generation
- Reproducible cryptographic key creation
- Seeded key generation for testing and simulation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e = 65537n])`

Generates deterministic RSA public and private keys.

#### Parameters
- `bits` (Number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (Optional BigInt): Public encryption exponent (default: 65537)

#### Returns
An object with two JSON Web Keys (JWK):
- `privateKey`: Contains full RSA private key components
- `publicKey`: Contains public key modulus and exponent

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = new Uint8Array(32).fill(0);  // Replace with your seed
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure
- `index.js`: Core library implementation
- `test.js`: Unit tests and example usage
- `package.json`: Project metadata and dependencies

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvements`)
3. Make your changes
4. Run tests
5. Submit a pull request

### Running Tests
```bash
npm test
```

## Performance and Limitations

- Key generation is computationally intensive
- Supports key sizes from 192 bits to large key sizes
- Primarily designed for deterministic, not cryptographically secure random generation

## Security

This library is intended for specific use cases. For production cryptographic needs, consider well-established cryptographic libraries.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Dependencies
- `workerpool`: For multithreaded prime generation

## Credits
Created by Andre Vallestero