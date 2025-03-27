# Deterministic RSA JS

**WARNING! This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK!**

## Project Overview

`deterministic-rsa-js` is a high-performance JavaScript library for generating deterministic RSA key pairs. The library provides a robust, performant solution for creating RSA keys based on seed values, specifically designed for scenarios requiring predictable key generation.

### Key Features
- 🚀 High-Performance RSA Key Generation
- 💻 Pure JavaScript Implementation
- 🔢 Utilizes Native BigInt for Precision
- 🧵 Multithreaded Prime Generation
- 📊 Deterministic Key Derivation
- 🔐 JSON Web Key (JWK) Compatible Output

### Performance Advantages
- ~3x faster than comparable libraries
- Efficient parallel prime generation
- Optimized memory management
- Native BigInt integer handling

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total bit length of the RSA modulus (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (optional, BigInt): Public exponent (default: 65537)

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

console.log(keyPair.publicKey);  // Public key in JWK format
console.log(keyPair.privateKey); // Private key in JWK format
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

### Running Tests
```bash
node test
```

### Guidelines
1. Ensure all tests pass
2. Follow existing code style
3. Add tests for new functionality
4. Update documentation

## Performance Optimization Roadmap

The library has several planned optimizations:
- Improved prime checking algorithms
- Native Node.js crypto integration
- Alternative pseudo-random number generation techniques

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Disclaimer

**⚠️ Cryptographic Security Warning**
While this library is designed with performance in mind, it has not been fully verified for cryptographic security. Use with caution and at your own risk in production environments.