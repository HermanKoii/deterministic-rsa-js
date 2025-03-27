# Deterministic RSA JS

## Project Overview

`deterministic-rsa-js` is a high-performance, vanilla JavaScript library for generating deterministic RSA keys. Unlike traditional RSA key generation methods, this library offers unique features:

- **Deterministic Key Generation**: Allows generating RSA keys from deterministic seeds
- **High-Performance**: ~3x faster than existing implementations
- **Native JavaScript**: Uses native `BigInt` for precise integer handling
- **Multithreaded Prime Generation**: Parallel processing for improved key generation speed
- **JSON Web Key (JWK) Compatible**: Outputs keys in standard JWK format

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

**Prerequisites:**
- Node.js version supporting BigInt (v10.4.0+)
- Workerpool library (included as a dependency)

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates deterministic RSA public and private keys.

**Parameters:**
- `bits` (number): Total number of bits for the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic prime generation
- `e` (BigInt, optional): Public encryption exponent, defaults to 65537n

**Returns:**
An object with `privateKey` and `publicKey`, both formatted as JSON Web Keys (JWK)

**Example:**
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit RSA key
const seed = crypto.randomBytes(32);
const { privateKey, publicKey } = await rsaGenKeys(2048, seed);
```

## Usage Notes

- The library uses a seeded pseudo-random number generator
- Prime generation is multithreaded using `workerpool`
- Keys are generated deterministically based on the provided seed
- All cryptographic operations are performed using native JavaScript `BigInt`

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Unit tests and example usage
- `package.json`: Project configuration and dependencies

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

**Running Tests:**
```bash
node test
```

## Performance Considerations

This library is optimized for:
- Fast random number generation
- Efficient prime checking
- Minimal garbage collection
- Parallel prime generation

## Roadmap

Current TODO items:
- Optimize prime checking implementation
- Add native Node.js crypto integration
- Explore alternative PRNGs

## License

MIT License. See the `LICENSE` file for details.

## Disclaimer

**WARNING:** This project has not yet been verified to be cryptographically secure. Use at your own risk.

## Resources

Detailed technical references and research papers are linked in the source code comments.