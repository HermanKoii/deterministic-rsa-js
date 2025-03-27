# deterministic-rsa-js

**WARNING! This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK!**

## Project Overview

`deterministic-rsa-js` is a high-performance JavaScript library for generating deterministic RSA keys using native BigInt operations. It provides a fast and efficient method for creating RSA key pairs based on mnemonic keys, with significant performance advantages over existing solutions.

### Key Features
- Native BigInt support for precise integer handling
- Multithreaded prime generation for improved performance
- Optimized random number generation
- Memory-efficient design
- ~3x faster than comparable libraries like node-forge

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js 12.0.0 or higher (with native BigInt support)
- Recommended: Workerpool for parallel processing (included in dependencies)

## API Reference

### Key Generation Methods

#### `generateKey(mnemonic: string, options?: Object): RSAKeyPair`
Generates a deterministic RSA key pair from a mnemonic seed.

**Parameters:**
- `mnemonic`: A string seed for deterministic key generation
- `options` (optional): Configuration object
  - `bits`: Key size (default: 2048)
  - `e`: Public exponent (default: 65537)

**Returns:** An object containing:
- `publicKey`: The generated public key
- `privateKey`: The generated private key

**Example:**
```javascript
const { generateKey } = require('deterministic-rsa-js');

const keyPair = generateKey('your secret mnemonic phrase');
console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

### Configuration

#### Environment Variables
- `DEBUG`: Set to `true` to enable verbose logging
- `WORKER_POOL_SIZE`: Configure number of worker threads (defaults to CPU core count)

## Repository Structure

- `index.js`: Main library entry point
- `test.js`: Test suite for library functionality
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Performance Optimizations

The library implements several performance enhancements:
- Native BigInt handling
- Parallel prime generation
- Efficient random number generation
- Preallocated memory buffers

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Running Tests
```bash
npm test
```

## Roadmap / Future Improvements

- Implement advanced prime checking algorithms
- Add native Node.js crypto integration
- Explore alternative Pseudo-Random Number Generators (PRNG)

## License

Distributed under the MIT License. See `LICENSE` file for more information.

## Disclaimer

**Security Warning:** This library is currently in beta. It has not been fully audited for cryptographic security. Use with caution in production environments.

## Resources

For more technical details, check out the extensive list of resources in the original README, covering cryptography, prime generation, and JavaScript performance techniques.