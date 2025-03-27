# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library for generating deterministic RSA key pairs using seeded random prime generation. Unlike typical randomized key generation, this library allows you to reproducibly generate RSA keys from a consistent seed, making it ideal for scenarios requiring predictable key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌱 Seed-based prime number generation
- 🔢 Configurable key bit lengths
- 🌐 Compatible with Web Crypto standards (JWK format)
- 🚀 Multithreaded prime generation
- 🔒 Cryptographically secure prime number testing

### Use Cases
- Reproducible key generation for testing
- Consistent key derivation in distributed systems
- Predictable cryptographic key management

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, e = 65537n)`

Generates deterministic RSA public and private keys.

#### Parameters
- `bits` (number): Total bits for RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537

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
- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies

## Dependencies
- `workerpool`: For multithreaded prime generation

## Performance Notes
- Key generation is deterministic and may take several seconds for large key sizes
- Uses multithreading to improve prime generation performance
- Miller-Rabin primality testing ensures cryptographic security

## Contributing
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Testing
Run tests using:
```bash
npm test
```

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Security
While this library provides deterministic key generation, always consult cryptography experts for mission-critical applications.