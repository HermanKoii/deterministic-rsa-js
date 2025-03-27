# deterministic-rsa-js 

## 🚨 Warning
**This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK!**

## Project Overview

`deterministic-rsa-js` is a high-performance, vanilla JavaScript library for generating deterministic RSA keys. Unlike traditional RSA key generation methods, this library offers unique advantages:

- **Deterministic Key Generation**: Create reproducible RSA keys from consistent seed inputs
- **Ultra-Fast Performance**: ~3x faster than comparable libraries like `node-forge`
- **Multithreaded Prime Generation**: Parallel prime number generation for improved speed
- **Native BigInt Support**: Leverages JavaScript's native BigInt for efficient large number handling

### Key Features
- Generates RSA keys using native JavaScript capabilities
- Supports customizable key bit sizes (minimum 192 bits)
- Uses multithreading with `workerpool` for parallel prime generation
- Returns keys in standard JSON Web Key (JWK) format
- Optimized memory allocation and type management

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates RSA key pairs deterministically.

#### Parameters
- `bits` (number): Total number of bits in the RSA modulus (must be multiple of 32, min 192)
- `seed` (Uint8Array): 32-byte seed for deterministic prime generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

#### Returns
An object containing:
- `privateKey` (JsonWebKey): Complete private key with all RSA components
- `publicKey` (JsonWebKey): Public key with modulus and exponent

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.randomBytes(32);  // Or your own deterministic seed
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT License details

## Performance Optimizations

The library implements several performance enhancements:
- Native BigInt for precise integer handling
- Multithreaded prime generation
- Optimized random number generation
- Preallocated buffers to reduce garbage collection

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Running Tests
```bash
node test
```

## Upcoming Improvements

- Optimized prime checking implementations
- Native Node.js crypto integration
- Alternative Pseudo-Random Number Generator (PRNG) methods

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Acknowledgements

Special thanks to the open-source community and the various cryptographic resources that made this project possible.