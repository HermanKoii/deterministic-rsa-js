# deterministic-rsa-js

**WARNING! This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK!**

## Project Overview

`deterministic-rsa-js` is a high-performance JavaScript library for generating deterministic RSA keys using native BigInt and advanced optimization techniques. Unlike traditional RSA key generation libraries, this implementation offers:

- 🚀 **Blazing Fast Performance**: Approximately 3x faster than existing solutions
- 🔬 **Deterministic Key Generation**: Generate reproducible RSA keys from a seed
- 💻 **Native JavaScript**: Leverages native BigInt for efficient large integer operations
- 🧵 **Multithreaded Prime Generation**: Parallel prime generation with 50% speedup
- 🔒 **JSON Web Key (JWK) Compatible**: Outputs keys in standard JWK format

### Key Features
- Generate RSA keys of configurable bit lengths
- Seeded key generation for reproducibility
- Optimized random number generation
- Miller-Rabin primality testing
- Multithreaded prime generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js version 14.x or higher
- Native support for BigInt

## API Reference

### `rsaGenKeys(bits, seed[, e])`

Generates deterministic RSA key pairs.

#### Parameters
- `bits` (number): Total modulus bit length (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for reproducible key generation
- `e` (BigInt, optional): Public exponent, defaults to 65537n

#### Returns
A Promise resolving to an object with `privateKey` and `publicKey` (JWK format)

#### Example
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit RSA key pair
const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);

console.log(keyPair.publicKey);
console.log(keyPair.privateKey);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Library test suite
- `package.json`: Project configuration and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch for your feature
3. Implement your changes
4. Write or update tests
5. Run tests with `node test`
6. Submit a pull request

### Testing

To run tests:
```bash
node test
```

## Future Roadmap

- [ ] Optimized prime checking implementation
- [ ] Native Node.js crypto integration
- [ ] Alternative Pseudo-Random Number Generator (PRNG)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Disclaimer

**WARNING!** This library has not been fully verified for cryptographic security. Use at your own risk and consult security experts for critical applications.