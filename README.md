# deterministic-rsa-js

## Project Overview

**deterministic-rsa-js** is a lightweight JavaScript library for generating deterministic RSA key pairs using seeded random prime generation. Unlike traditional RSA key generation, this library allows you to reproducibly generate RSA keys from a consistent seed, making it ideal for cryptographic applications that require predictable key generation.

### Key Features

- 🔐 Deterministic RSA key generation
- 🌱 Seed-based prime number generation
- 🚀 Multithreaded prime generation
- 🔢 Configurable key bit lengths
- 📦 Generates JSON Web Key (JWK) formatted keys
- 💻 Pure JavaScript implementation

### Use Cases

- Reproducible key generation for testing
- Cryptographic systems requiring consistent key derivation
- Blockchain and distributed systems
- Secure, predictable key generation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic prime generation
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Create a 2048-bit key with a specific seed
const seed = crypto.getRandomValues(new Uint8Array(32));
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### Running Tests

```bash
npm test
```

## Performance and Limitations

- Suitable for key generation up to 4096 bits
- Uses multithreaded prime generation
- Relies on JavaScript's BigInt and workerpool

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

Created by Andre Vallestero