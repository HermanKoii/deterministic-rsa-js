# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library that provides deterministic RSA key generation using seeded random number generation. This library enables developers to generate reproducible RSA key pairs with precise control over the key generation process.

### Key Features
- 🔑 Deterministic RSA Key Generation
- 🌱 Seed-based Prime Number Generation
- 🧵 Multithreaded Prime Generation
- 🔢 Configurable Key Bit Lengths
- 🛡️ Probabilistic Primality Testing
- 🌐 JSON Web Key (JWK) Compatible Output

### Use Cases
- Cryptographic testing and simulation
- Reproducible key generation for distributed systems
- Blockchain and decentralized applications
- Cryptographic research and development

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js (version 14.0.0 or higher)
- Compatible with modern browsers supporting BigInt

## API Reference

### `rsaGenKeys(bits, seed, e = 65537n)`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent (default: 65537)

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Repository Structure
- `index.js`: Core library implementation
- `test.js`: Test suite for library functions
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

### How to Contribute
1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### Running Tests
```bash
npm test
```

## Performance Considerations
- Uses multithreaded prime generation
- Implements efficient Miller-Rabin primality testing
- Optimized modular arithmetic algorithms

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer
While this library provides robust key generation, always consult cryptography experts for mission-critical security implementations.