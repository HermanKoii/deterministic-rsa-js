# Deterministic RSA JS

## Project Overview

Deterministic RSA JS is a lightweight JavaScript library that provides deterministic RSA key generation using a seeded approach. Unlike traditional RSA key generation methods that rely on randomness, this library allows you to generate reproducible RSA keys from a consistent seed.

### Key Features
- 🔑 Deterministic RSA key generation
- 💻 Pure JavaScript implementation
- 🔒 Supports configurable key sizes
- 🧵 Multithreaded prime generation using `workerpool`
- 🔍 Compatible with JSON Web Key (JWK) standard

### Why Deterministic RSA?
Traditional RSA key generation involves random number generation, which makes key reproduction impossible. This library solves that by allowing predictable key generation from a deterministic seed, which is crucial for scenarios requiring reproducible cryptographic keys.

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

## Prerequisites
- Node.js (version 12.0.0 or higher)
- A modern browser with BigInt support

## API Reference

### `rsaGenKeys(bits, seed, e = 65537n)`

Generates deterministic RSA key pairs.

#### Parameters
- `bits` (number): Total bit size of the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic prime generation
- `e` (BigInt, optional): Public exponent, defaults to 65537

#### Returns
An object with two JWK-formatted keys:
- `privateKey`: Complete RSA private key
- `publicKey`: RSA public key

#### Example

```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

async function generateKeys() {
  const seed = crypto.getRandomValues(new Uint8Array(32));
  const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
  console.log(privateKey, publicKey);
}
```

## Repository Structure

- `index.js`: Core library implementation
- `test.js`: Unit and integration tests
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT License details

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

- The library uses Miller-Rabin primality testing for probabilistic prime generation
- Key generation can be computationally intensive for very large key sizes
- Recommended for controlled, reproducible cryptographic scenarios

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

Developed by Andre Vallestero as part of the Open Koi project.