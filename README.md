# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA keys using a seeded approach. Unlike traditional RSA key generation methods, this library allows you to reproduce the exact same RSA key pair when given the same input seed, making it useful for scenarios requiring reproducible cryptographic key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌱 Seed-based prime number generation
- 🚀 Multithreaded prime generation
- 🔒 Compatible with JSON Web Key (JWK) format
- 🧮 Configurable key bit lengths

### Use Cases
- Cryptographic systems requiring reproducible keys
- Blockchain and distributed systems
- Testing and development environments
- Security protocols with controlled key generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js version 12 or higher
- Modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed[, e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total bit length of the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (BigInt, optional): Public encryption exponent (default: 65537)

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example Usage
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // Prints the public key
console.log(keyPair.privateKey); // Prints the private key
```

### Utility Functions (Internal)
- `seededRandPrime(bits, seed, exp, small_primes)`: Generates a seeded prime number
- `millerRabin(n, k)`: Primality testing
- `modExp(a, b, n)`: Modular exponentiation
- `biToB64url(num)`: BigInt to base64url conversion

## Repository Structure
- `index.js`: Main library implementation
- `package.json`: Project metadata and dependencies
- `test.js`: Test suite for the library
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Run tests (`npm test`)
5. Commit your changes (`git commit -m 'Add some feature'`)
6. Push to the branch (`git push origin feature/improvement`)
7. Open a Pull Request

### Running Tests
```bash
npm test
```

## Performance and Limitations

- Generates prime numbers using a seeded pseudorandom number generator
- Supports key sizes from 192 bits to several thousand bits
- Uses Miller-Rabin primality testing with adaptive test rounds

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

Created by Andre Vallestero