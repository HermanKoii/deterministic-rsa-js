# Deterministic RSA Generator (JavaScript)

## Project Overview

`deterministic-rsa-js` is a lightweight JavaScript library for generating deterministic RSA key pairs using seeded prime generation. Unlike traditional RSA key generation, this library allows you to reproducibly generate RSA keys from a consistent seed, making it ideal for cryptographic applications that require predictable key generation.

### Key Features
- 🔑 Deterministic RSA key generation
- 🌱 Seed-based prime number generation
- 🚀 Multi-threaded prime generation using `workerpool`
- 🔢 Configurable key size and public exponent
- 🔒 Follows JSON Web Key (JWK) standard for key representation

### Use Cases
- Reproducible cryptographic key generation
- Blockchain and distributed systems
- Deterministic wallet generation
- Testing and simulation environments

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js version 14.x or higher
- Modern JavaScript environment supporting BigInt and Web Workers

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

#### Parameters
- `bits` (number): Total key size in bits (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic generation
- `e` (BigInt, optional): Public exponent (default: 65537n)

#### Returns
An object with two keys:
- `privateKey` (JsonWebKey): Complete private RSA key
- `publicKey` (JsonWebKey): Public RSA key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);  // JWK public key
console.log(keyPair.privateKey); // JWK private key
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Unit tests and examples
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/amazing-improvement`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/amazing-improvement`)
5. Create a Pull Request

### Running Tests

```bash
npm test
```

## Performance Considerations

- Uses multi-threaded prime generation
- Implements efficient modular arithmetic algorithms
- Miller-Rabin primality testing with adaptive iteration count

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

Developed by Andre Vallestero